学习给搜索框做节流、防抖搜索

一、作用：可优化高频率执行代码的一种方式，避免不断调用 绑定在事件上的回调函数，降低前端性能等；

二、运用场景：
防抖：
（1）搜索框搜索输入-在用户最后一次输入完后，再去发送请求；
（2）手机号、验证等的输入检测；
（3）窗口大小 resize，只需窗口调整好后，计算窗口大小，防止反复渲染；

节流：
（1）滚动加载，加载更多或者滚动到底部监听；
（2）搜索框的联想功能等；

三、防抖、节流的区别及写法：

1、搜索框防抖（Debounce）

（1）指在事件触发后等待一段时间，如果在这段时间内再次触发了同一个事件，就取消之前的定时器，重新再计算定时器；只有在设定时间内没有再次触发事件时，才执行相应操作；

（2）每次事件触发时，先清除之前的定时器，然后设置一个新的定时器。

写法：

const DebouncedInput = () => {
const [searchTerm, setSearchTerm] = useState('');

//使用 useState 钩子来声明一个名为 searchTerm 的状态变量，把初始值为空字符串，并使用 setSearchTerm 存他更新该状态后的变量

useEffect(() => {
const timer = setTimeout(() => {
console.log('执行搜索：', searchTerm);
}, 500);

    return () => clearTimeout(timer);

}, [searchTerm]);

//用 useEffect 来实现防抖效果,当 searchTerm 发生变化时，useEffect 就会执行，设置一个为 500 毫秒的定时器，在 500 毫秒后执行操作。当 useEffect 返回一个清除定时器的函数，以确保每次搜索前都清除之前的定时器。

const handleInputChange = (e) => {
setSearchTerm(e.target.value); // 用于处理点击 button 后执行搜索操作，更新搜索词。
};

return (
<input
      type="text"
      placeholder="請輸入名字搜索"
      value={searchTerm}
      onChange={handleInputChange}
    />
);
};

export default DebouncedInput;

2、搜索框节流（Throttle）

（1）指在设定的时间内只允许事件触发一次；在一段时间内多次触发的事件，也只能有第一次触发后才执行相应操作，之后的触发会被忽略，直到过了设定的时间后才能再次触发；

（2） 每次事件触发时，设置一个定时器，在定时器执行之前的事件触发会被忽略。

写法：

const ThrottledInput = () => {
const [searchTerm, setSearchTerm] = useState('');
//同上，使用 setSearchTerm 来存更新后的变量

useEffect(() => {
const timer = setTimeout(() => {
// 执行搜索操作，比如发送请求到服务器

      console.log('执行搜索：', searchTerm);
    }, 500);

    return () => clearTimeout(timer);

}, [searchTerm]);
// 返回一个清除定时器的函数，当 searchTerm 变化时重新执行 useEffect

const handleInputChange = (e) => {
setSearchTerm(e.target.value);
};

return (
<input
      type="text"
      placeholder="請輸入名字搜索"
      value={searchTerm}
      onChange={handleInputChange}
    />
);
};

export default ThrottledInput;
