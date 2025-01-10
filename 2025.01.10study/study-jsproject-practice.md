## 分析 Js Practice Project

## html 部分：

1、建一个 index.html、script.js、style.css 的文件

2、在 html 的 body 层

写页面的内容：
分析 ui，有两层包裹：
第一层是外层容器包裹 整个进度条+底部的 button，class 命名为 container
底部的 button：也给个 id：一个是 prev，另一个是 next

第二层是 包裹整个进度条，class 命名为 progress_container(进度条容器)
第二层里面包裹了圈圈的数字、进度条：

圈圈的数字：class 命名为 circle，把第一个加多个 active 的动态命名

进度条 class 命名为 progress，同时给个 id 为 progress；

除了页面内容，引入使用 script 的标签，src 来引用 js 的文件使用

## 2、css 的部分（根据 ui 的来给出样式）：

（1）首先定义 root 的样式，可以用于全局的样式变量使用：

//其中的 line-border 命名为当前 currentActive 的样式
//line-border-empty 定义的是其他不属于 currentActive 即为空状态下的样式
//border-box 通用于所有的元素

    :root {
    --line-border: #aad09b;
    --line-border-empty: #efd4af;
    }
    * {
      box-sizing: border-box;
    }

（2）接着定义 body 的部分：

整体的 body 跟着 ui：使用 flex 布局，居中所有的内容、高度设为 100vh 可见、外边距为 0，超出部分使用 hidden 显示；

（3）定义外层容器 container 给只要给个字体的位置：text-align 居中；

（4）定义外层包裹进度条和圈圈数字的， class 命名为 progress_container，这里是显示进度条，需要写两个样式，一个是初始状态下的样式、一个是点击后显示出进度条的样式；

//progress_container 对应的是包裹进度条和圈圈数字的外层
//加多一个 before 表示的是点击前的颜色，这里的背景色使用上面 root 根元素定义的样式为 empty 的样式，给了个 absolute 的绝对定位，transform 设为 y 轴上往上挪 50%的位置，z-index 为-1，显示出来的样式为 progress 位置在圈圈数字的 y 轴中间、且在数字底部不会遮挡；
//progress 的样式表示点击后的进度条颜色

    .progress_container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 30px;
    max-width: 100%;
    width: 350px;
    position: relative;
    }
    .progress_container::before {
      content: "";
      background-color: var(--line-border-empty);
      position: absolute;
      top: 50%;
      left: 0;
      transform: translateY(-50%);
      height: 4px;
      width: 100%;
      z-index: -1;
    }
    .progress {
      background-color: var(--line-border);
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      height: 4px;
      width: 0%;
      z-index: -1;
    }

（5）定义数字那层 class 为 circle 的这层，还有 class 为.circle.active 定义一个选中后的圈圈的边框色（样式为根元素定义样式的 line-border）

    .circle.active {
      border-color: var(--line-border);
    }

（6）定义点击的 button 样式 class 为.btn:active （点击时）给出的是缩小为 98%、.btn:focus（button 聚焦时）把外框设为 0、.btn:disabled（无法点击时）背景色设为 empty 的颜色；

## 3、js 的部分 逻辑：

（1）
