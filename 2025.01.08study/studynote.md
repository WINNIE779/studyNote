## 总结 hooks&ahooks 的用途分类

## 与管理状态相关的：

useState：管理组件内部的状态；
useContext：管理可共享全局的状态逻辑；
useReducer:管理复杂的状态逻辑；

## 处理副作用相关的有：

useEffect：处理组件中的副作用，获取数据、监听事件等；
useLayoutEffect：在浏览器布局、绘制之后会同步执行；
用法，如：

    useLayoutEffect(() => {
      // 组件挂载

      return () => {
        // 组件挂载
      };
    }, []);

useEffectEvent：可以用于特定事件的绑定执行副作用，如滚动事件；
用法，如：

    const A = () => {
      // 监听滚动事件
      useEffectEvent(
        "scroll", // 事件回调
        (event) => {
          // 滚动时执行的操作
        }
      );

      return <div>...</div>;
    };

## 节流防抖、优化性能相关：

hooks：
useThrottle：节流，限制操作频繁触发，指定在一个期间内只能触发一次；
useDebounce：防抖，频繁多次触发，只执行指定时间的最后一次；

ahooks：
useThrottleFn：函数节流；
useThrottleEffect：处理节流副作用；
useDebounceFn：函数防抖；
useDebounceEffect：处理防抖副作用；

## 缓存、优化性能相关：

useMemo：缓存计算结果的值，依赖项发生变化时，才会重新计算渲染；
useCallback：记忆化函数，避免不必要的函数创建；
useRef：缓存引用、缓存值或对象，可以避免多次渲染创建，方便之后在组件渲染之间保持持久化值；

## 定时器管理相关：

ahooks：
useTimeout：用于延迟执行触发；
useRafTimeout：延迟执行触发，与 useTimeout 相比，页面不见时会停止；
useInterval：定时器设置处理；
useRafInterval：定时器设置处理，与 useInterval 对比，页面不见时会停止执行；

## 轮询接口用途相关：

useRequest：支持轮询、节流、防抖；
useInterval：与定时器相关，可以用于定时轮询接口；
usePolling：需要用到 start、stop 来控制轮询的开始停止，期间轮询管理时间参数 interval 来设定时间；
useTimeout：可以用于手动触发轮询接口；
