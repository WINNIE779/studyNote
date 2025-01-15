## 分析 skill 的接口逻辑

1、先定义接口需要的参数

//把 IPagesDto 扩展在 IntentsParams，接口参数为关键词 keyword、collectionType 的选择、pageIndex 当前页、pageSize 页面可获取的数据条数
export interface IntentsParams extends IPagesDto {
Keyword: string;
CollectionType: SkillType[];
}

//定义接口返回拿到的数据
export interface IntentsDto {
result: IntentsResultProps[];
totalCount: number;
}

export interface IPagesDto {
PageSize: number;
PageIndex: number;
}

//定义 collectionType 的枚举
export enum SkillType {
QuestionAndAnswerType,
KnowledgeType,
TableType,
}

//对应上面枚举的值
export const SkillTextType = {
[SkillType.QuestionAndAnswerType]: "問答類",
[SkillType.KnowledgeType]: "知識類",
[SkillType.TableType]: "表格類",
};

//定义接口 reslut 返回的类型
export interface IntentsResultProps {
id: number;
chatID: number;
name: string;
description?: string;
collectionType: SkillType;
createdBy?: number;
createdDate: string;
lastModifiedBy?: number;
lastModifiedDate?: string;
collections?: string;
trainStatus?: number;
flowStatus?: boolean;
status?: ISkillCardStatus;
}

2、通过 api 获取接口

//通过上面的类型定义到接口获取
export const GetSkillIntentsApi = async (data: IntentsParams) => {
const response = await api.get<IntentsDto>("/api/SmartChat/intents", {
params: data,
});

return response.data;
};

3、在组件里定义初始值,通过用 useState 来把初始值或者更新后的数据进行存储

//定义一个 CombinedDto，结合 IntentsDto, ISearchDto, IPagesDto 的类型；
interface CombinedDto extends IntentsDto, ISearchDto, IPagesDto {}

//用 useState 来存储 cardIntentDto 来获取，并且根据上面的类型给出初始值
const [cardIntentDto, setCardIntentDto] = useState<CombinedDto>({
PageIndex: 1,
PageSize: 18,
Keyword: "",
result: [],
totalCount: 0,
CollectionType: [
SkillType.QuestionAndAnswerType,
SkillType.KnowledgeType,
SkillType.TableType,
],
});

4、封装一个方法获取新的数据

const updateGetCardIntents = (key: keyof CombinedDto, value: any) => {
setCardIntentDto((prev) => ({
...prev,
[key]: value,
}));
};

5、获取调用 api 的方法：

进入页面后触发方法：
把调用 api 的方法需要获取的参数传入方法：
pageIndex：定义当前页面；
pageSize：定义每页中的数据条数；
keyword：定义关键词；
collectionDto：因为进入页面后会全选三种类型，所以初始值为全选，当类型有选择也会改变获取的数据对应的类型；
首先把
接着调用 api 接口:(把上面的参数传进去)
获取成功后：把新的数据更新到封装的方法里
获取失败后：恢复初始值，返回的 result 需要设为空数组。

const getSkillIntentsCard = (
PageIndex: number = cardIntentDto.PageIndex,
PageSize: number = cardIntentDto.PageSize,
type: SkillType[],
searchText: string
) => {

setCardIntentDto((prev) => ({
...prev,
}));

    GetSkillIntentsApi({
      PageIndex,
      PageSize,
      Keyword: searchText ?? "",
      CollectionType: type,
    })
      .then((res) => {
        updateGetCardIntents("totalCount", res.totalCount);
        updateGetCardIntents("result", res.result);
        updateGetCardIntents("PageIndex", PageIndex);
        updateGetCardIntents("PageSize", PageSize);
      })
      .catch(() => {
        message.error("獲取失敗");

        updateGetCardIntents("totalCount", 0);
        updateGetCardIntents("result", []);
        updateGetCardIntents("PageIndex", PageIndex);
        updateGetCardIntents("PageSize", PageSize);
      });

};

useEffect(() => {
getSkillIntentsCard(
cardIntentDto.PageIndex,
cardIntentDto.PageSize,
cardIntentDto.CollectionType,
cardIntentDto.Keyword
);
}, []);
