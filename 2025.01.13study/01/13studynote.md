## 分析 background js project 的逻辑

同样分为 html、css、js 部分实现

## html 部分

同样的格式在 body 部分写一个外层包裹里面的 4 张 pic

外层的容器的 class 命名为 container

里层的每个 div
1、都给同样的 class 名字为 pic 第一个加多个 active（这个为初始默认的 active 样式）
2、给每个 div 就是每张 pic 不同的 id
3、给出图片的 url

底部 引入使用 script 的标签，src 来引用 js 的文件使用

## css 部分

根据 html 里的每一层 class 来给出相应的样式

底部的 pic 和加了 active 的：找出他们同类的样式写在 pic 里，active 的部分只要加 flex 的动态

## js 部分的实现

     const pics = document.querySelectorAll(".pic");//使用js的dom元素方法来获取每个带有.pic的pics

     let currentId = 1; // 初始当前的id为1

     // 接着用addEventListener给每个pic添加点击的监听
     pics.forEach((pic) => {
       pic.addEventListener("click", () => {

         currentId = pic.id;
         //当发生click后，当前的id就会等于监听到的id，更新到当前的currentId上

         // 使用forEach来遍历所有带pic元素的图片
         pics.forEach((pic) => {
           if (pic.id === currentId) {
             pic.classList.add("active");  // 如果监听到的pic.id等于当前id的话，添加active类的样式给他
           } else {
             pic.classList.remove("active"); // 如果监听到的pic.id不等于当前id的话，就会移除pic的active类的样式
           }
         });
       });
     });
