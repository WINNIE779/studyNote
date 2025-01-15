## ahooks 学习笔记：

## useLockFn

用于异步函数不会被同时执行多次，避免重复调用

使用场景：

用法：

可以添加在提交表单发送请求时，可以避免用户多次点击、直到上次调用完才会再次执行；
或者获取调用接口时，可以避免出现重复触发的情况；

import { useLockFn } from 'ahooks';
//从 ahooks 引入 useLockFn

const handleButton = useLockFn(async () => {
await message.success("ok");
});

<button onClick={handleButton}>完成</button>

但是 useLockFn 不可以在组件需要初始渲染时使用，应在需要手动触发时；适用异步函数，同步函数是不会进行触发；

## useUpdate 与 useState 对比

useUpdate：

用于触发组件的强制重新渲染，但不会去改变到组件的状态，不会返回一个状态值，而是返回一个函数，调用这个函数才会触发组件的更新；

useState：

用于在组件中去定义、或者管理更新组件的状态，并触发组件进行重新渲染；

## useThrottle

用于需要限制某些操作频繁触发的时候，会指定在一个期间内只能触发一次，優化性能；

useThrottle 与 useDebounce 对比：
useDebounce 是给出一个时间，达到这个时间后的触发才会执行；
useThrottle 是会给出一个时间间隔，按固定的时间间隔从而去触发。

使用场景：

//這裡的用法可以防止連續點擊 button，來控制觸發事件的發生，同樣也可以適用在輸入框的搜索

import { useThrottle } from 'ahooks';//引入 useThrottle

const handleClick = useThrottle(() => {
console.log("click");//触发后打印出 click
}, 1000);//指定在 1 秒内只触发一次

return <button onClick={handleClick}>Click</button>;

## useBoolean

用於管理布尔状态，适用于频繁改变布尔值状态下的场景；

useBoolean 与 useState 来管理布尔值的区别：

使用 useBoolean：

import { useBoolean } from 'ahooks';

const [isOpen, { setTrue, setFalse }] = useBoolean(false);//定义 open 的 true 和 false 的初始值都为 false

return(

  <div>
      <button onClick={setTrue}>Open</button>//直接触发setTrue来表示打开
      <button onClick={setFalse}>Close</button>//直接触发setFalse来表示
  </div>
)

使用 useState 来管理布尔值状态：

const [isOpen, setIsOpen] = useState(false);//使用 useState 来管理 open 的状态

return(

  <div>
     <button onClick={() => setIsOpen(true)}>Open</button>//当为open的情况下，需要把true给到setIsOpen去更新状态
     <button onClick={() => setIsOpen(false)}>Close</button>//同样当为close的情况下，需要把false给到setIsOpen去更新状态
  </div>
)

对比：
同时都具有管理布尔值状态的场景；

不同之处：
useBoolean：只适用于简单的布尔值状态的场景；
useState：能支持对象、数组、字符串等的类型，更能通用与逻辑中。
