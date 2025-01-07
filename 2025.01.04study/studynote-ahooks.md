## 学习 ahooks：

ahooks 提供的定时器分别为：useInterval、useRafInterval、useTimeout、useRafTimeout

## useInterval

用于处理定时器

使用场景：轮询接口需要定时去获取新数据、或者加载进度条、定时更新状态数据时；

useInterval(() => {
setCount((prev) => prev + 1);
}, 1000);

//这里表示每间隔一秒会增加计时

参数：
callback（需要执行回调函数）
delay（设置定时器的间隔时间）
immediate(这个为可选参数，指定是否在首次渲染时执行回调函数)

可以在组件卸载时，调用 clearInterval()自动清理定时器，避免内存泄露

## useRafInterval

勇于优化性能

使用场景：当页面不见时暂时执行（如图片轮播、页面不见时可停止轮播图片、优化性能）

useRafInterval(() => {
updatePicture();
}, 1000);

//这里同样表示每间隔一秒进行更新加载，但是当页面不见时便会停止执行

## useTimeout

用于需要延时去执行

使用场景：页面加载需要延时触发执行渲染、或者需要定时去执行跳转或弹出对应的提示等；

useTimeout(() => {
setShowMessage(true);
}, 1000);

//延时 2 秒会触发 message

## useRafTimeout

用于需要延时执行，又同时需要页面不见时暂停执行的场景，恢复可见后又可以执行；

// 延迟 3 秒后更新"3！"到 message，但是当页面不可见时就会暂停
useRafTimeout(() => {
setMessage("3！");
}, 3000);
