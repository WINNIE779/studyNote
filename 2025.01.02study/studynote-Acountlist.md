## 分析 list 的获取逻辑

1、先定义获取接口的参数

export interface IPageDtos {
pageIndex: number;//pageIndex(定义当前页)
pageSize: number;//pageSize（定义 list 每页的数据条数）
userName: string;//userName（定义的是搜索词）
}

export interface IAccount {
count: number;//接口对应的参数（数据总数）
userAccounts: IUserAccount[];//列表的数据（ IUserAccount 是每条用户数据的具体参数）
}

2、通过 api 获取接口（跟着接口的参数定义好后，把定义的类型给到去获取接口）

export const getAccountList = async (data: IPageDtos) => {
return (
await api.get<IAccount>(
`/api/Security/get?PageIndex=${data.pageIndex}&PageSize=${data.pageSize}&UserName=${data.userName}`
)
).data;
};

3、组件里获取 api 接口方法：

先用 useState 来管理 account 页面的数据：

type IAccountDto = IAccount & IPageDtos;（结合 IAccount 和 IPageDtos 类型，定义为 IAccountDto）

//接着定义一个初始值命名为 defaultAccount
const defaultAccount: IAccountDto = {
count: 0,
userAccounts: [],
pageIndex: 1,
pageSize: 10,
userName: "",
};

const [accountDto, setAccountDto] = useState<IAccountDto>(defaultAccount);

const fetchAccountList = (pageIndex = 1, pageSize = 10, userName = "") => {
setLoading(true);//触发后先开始加载

    getAccountList({ pageIndex, pageSize, userName })//接着调用getAccountList，将pageIndex, pageSize, userName传给api
      .then((res) => {
        setAccountDto((prev) => ({
          ...prev,
          pageIndex,
          pageSize,
          count: res?.count ?? 0,//判断成功后返回的数据总数是为undefined或者null的话显示为0
          userAccounts: res?.userAccounts ?? [],//判断列表的数据，如果为不存在就返回空的数组
        }));//成功获取后，用setAccountDto去更新最近的数据
      })
      .catch(() => {
        setAccountDto((prev) => ({
          ...prev,
          pageIndex,
          pageSize,
          count: 0,
          userAccounts: [],
        }));//获取失败的话，也是更新setAccountDto的状态，但是把count、userAccounts表示为0或者空数组的情况

        message.error("error")//获取失败返回error的提示
      })
      .finally(() => {
        setLoading(false);
      });//最后无论什么情况，都关闭加载状态

};

4、同时，获取列表的角色的接口：

也是先定义类型：

export interface IRole {
id: number;
createdDate: string;
modifiedDate: string;
name: string;
displayName: string;
systemSource: SystemSource;
description: string;
isSystem: boolean;
}

export interface IGetRole {
count: number;
roles: IRole[];//这里的 IRole 是定义角色的类型
}//获取每条数据角色的类型

const defaultRole: IGetRole = {
count: 0,
roles: [],
};//定义初始值

//用 useState 来存储获取角色数据的状态
const [roleDto, setRoleDto] = useState<IGetRole>(defaultRole);

const fetchRoleList = () => {
setLoading(true);//同样触发后先进入加载状态

    getRoleList({
      pageIndex: 1,//设置当前的页码为第一页
      pageSize: 2147483647,//这里表示的是获取所有数据，无限
      keyWord: "",//搜索的关键词不设置，默认值为空
      systemSource: SystemSource.SmartTalk,//枚举
    })//接着调用getRoleList
      .then((res) => {
        setRoleDto({
          count: res?.roles?.length ?? 0,//表示成功获取角色总数count，如果roles没有length的话默认为0
          roles:
            res?.roles.reverse().filter((item) => item.name !== "超级管理员") ??
            [],//如果获取到roles的话，把他们进行倒序排列，接着用filter来把其中名为"超级管理员"筛选过滤掉；如果roles为空则返回空数组。
        });
      })//调用成功后，更新setRoleDto的状态
      .catch((error) => {
        setRoleDto(defaultRole);
      })//获取失败的话，返回默认值到setRoleDto
      .finally(() => {
        setLoading(false);
      });//最后关闭加载状态

};

5、接着，用 useEffect 来监听 fetchAccountList、fetchRoleList

useEffect(() => {
fetchAccountList();
fetchRoleList();
}, []);//依赖项为空，表示已进入 account 页面就会开始渲染
