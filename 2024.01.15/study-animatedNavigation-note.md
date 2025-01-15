## 分析 Animated Navigation js project 的逻辑(动态路由)

同样分为 html、css、js 部分实现

## html 部分

同样的格式在 body 部分写一个外层包裹里面：

1、nav 的路由标签：这里包含了 button、以及点击 button 后有个动态的 menu 路由

2、这里用一个 container 来包裹主页面的 content，里面的内容 id 跟上面 routes 得 id 是对应的，这样后面写 js 逻辑实现，当 routes 的 id 跟 content 的 id 相等的话，就会给相等 id 的 content 加入 active 得样式显示，其他的就会被隐藏掉。

底部 引入使用 script 的标签，src 来引用 js 的文件使用

## css 部分

同样也是根据 html 里的每一层 class 来给出相应的样式

## js 部分的实现

分为两部分：
1、点击 button 后的处理；
document.addEventListener("DOMContentLoaded", () => {
//等完全加载并解析后再执行代码

       const toggleButton = document.getElementById("toggle");
       // 获取id=toggle的来切换按钮的DOM元素

       const routes = document.querySelector(".routes");
       // 通过id=routes来获取routes的

       const pics = document.querySelectorAll(".pic");
       // 获取所有id=pic图片的DOM元素列表

       toggleButton.addEventListener("click", () => {
         // 监听menu和close的切换，当触发click时会触发进入下面

         const menu = toggleButton.querySelector(".menu");
         // click之后会出发menu

         const close = toggleButton.querySelector(".close");
         // 顶部的button会变成id为close

         const isRoutesVisible = routes.style.display === "flex";
         // 接着判断菜单是否当前可见

         routes.style.display = isRoutesVisible ? "none" : "flex";
         // 如果菜单可见，就会隐藏掉；如果菜单不可见，就会显示出来

         menu.style.display = isRoutesVisible ? "block" : "none";
         // 根据菜单是否可见，显示或隐藏menu得选择

         close.style.display = isRoutesVisible ? "none" : "block";
         // 根据菜单是否可见，显示或隐藏关闭menu得选择
       });

2、点击 button 里面的路由菜单处理；

       routes.addEventListener("click", (event) => {
         // 给路由菜单绑定点击事件，当用户点击菜单项时触发以下逻辑

         const route = event.target;
         // 获取触发点击事件的目标元素

         if (route.classList.contains("route")) {
           // 判断目标元素是否具有"route"类名，确保只有菜单项被点击时执行逻辑

           event.preventDefault();
           // 阻止默认的链接跳转行为

           pics.forEach((pic) => {
             // 遍历所有图片元素，更新它们的显示状态

             if (pic.id === route.id) {
               // 如果图片的ID与点击的路由项的ID相同

               pic.classList.add("active");
               // 为对应图片添加"active"类，使其可见或高亮显示

             } else {
               pic.classList.remove("active");
               // 为不匹配的图片移除"active"类，隐藏或取消高亮
             }
           });
         }
       });
     });
