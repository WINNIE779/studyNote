
学习useCallBack：

主要用于优化组件的性能，可以避免不必要的重新渲染和函数的创建，特别是在将要从父组件传递给子组件回调函数的时候；

例如：



import React, { useState, useCallback } from 'react';

export const example = () => {
  const [count, setCount] = useState(0);

  
  
  //这里用useState来使用 useCallback 缓存 handleClick 函数，只有在 count 改变时才会重新创建这个函数



  const handleClick = useCallback(() => {
    console.log(count);
  }, [count]);



//这里的handleClick用useCallback来把改变的缓存下来，因为依赖的是原先的count，只有当count发生变化的时候才会重新进行创建，使用useCallback可以避免了每次click时的重新创建和渲染；



const handleClick = useCallback(() => {
    setCount(count + 1);
    console.log(count);
  }, [count]);

  const handleOnChange = useCallback(() => {
    setCount((prev) => {
      console.log(prev + 1);
      return prev + 1;
    });
  }, []);




//这里的handleClick和handleOnChange同样用了useCallback来，但是不同的是这里的依赖项一个是count一个则为空，当点击时button是时，区别：

1、handleClick虽然会显示set后的值，但是因为依赖项为count，所以打印出来的还是原先count的值，而不是更新后的值；

￼![R LO](https://github.com/WINNIE779/studyNote/assets/138740518/49fcad4a-0f1b-4f18-b67c-c665b6f10bea)


2、handleOnChange因为依赖项为空，只有count第一次渲染改变时会创建一次，但是不会重复性的去重新创建多一次或者重复渲染多一次，所以这里也可以打印出更新后的count跟count及时对应上；

￼![代 元素 主控台](https://github.com/WINNIE779/studyNote/assets/138740518/ee9c1a97-e6c8-4309-8f5e-fbfe1a756abc)


//当点击CC后点击BB后，会出现重复性的渲染

![主控台](https://github.com/WINNIE779/studyNote/assets/138740518/66710f3c-1b3d-47e8-ade4-f11d4b66c9ff)

￼
//但是相反：
￼
![元素](https://github.com/WINNIE779/studyNote/assets/138740518/2996b443-786e-4635-9f59-3a522ce870ff)



  return (
    <div>
      <p>{count}</p>
      <button onClick={() => setCount(count + 1)}>AA</button>
      <button onClick={handleClick}>BB</button>
      <button onClick={handleOnChange}>CC</button>
    </div>
  );
};






