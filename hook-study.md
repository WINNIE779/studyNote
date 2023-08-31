# React Hook

React中引用Hooks是提供了一种重用逻辑的方法，且可以让代码看起来更加整洁简单；最常用的是useEffect和useState。

## useEffect（使用效果）

useEffect是一个Hook,只能使用在组件顶层或者自己的hook中调用；（不能在循环、条件内使用）

用法：

1、如果没有的话代表每次执行组件函数时都会执行副作用函数，如：

    useEffect(() =>{} )
    
2、如果加入[]空数组的话，代表副作用函数只会执行一次，如：

     useEffect(() =>{},[] )

3、如果加入[依赖项]，依赖项变化时，副作用函数会执行，如：

    useEffect(() =>{},[依赖项] )

    
## useState（使用状态）
    
useState在组件的顶层调用来声明状态变量。

用法：

1、


    import { useState } from 'react';

    function MyComponent() {
      const [age, setAge] = useState(18);
      const [name, setName] = useState('ABC');
      
约定const[a，seta]是像使用数组解构一样命名状态变量；

useState返回一个包含两项的数组：

（1）设置变量的当前状态，最初设置提供的是初始状态；
（2）set函数可以将其更改为任何值且响应交互；

使用set状态下来调整该函数，如：


    function handleClick() {
      setName('A');
    }
    
React会将存储下一个状态“A”，使用“A”来再次渲染组件，并更新到界面；但是set函数不会更改已执行代码中的的当前状态，仅是会影响下次从useState渲染开始返回的内容。


      
