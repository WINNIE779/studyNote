## 1、Layout Routes

需使用<outlet/>在每个子路由中作渲染，利用index作为索引，默认为子路由；

（1）Layout组件具有 <Outlet>和<Link>元素；且能呈现<Outlet>当前选择的路线。

（2）<Link>用于设置 URL 并跟踪浏览历史记录；当链接到内部路径时，都可以Link 使用a href=""；

（3）“布局路由”是一个共享组件，它在所有页面上插入通用内容，例如导航菜单。


## 2、操作渲染路由

（1）可使用Action作为点击触发路由的操作渲染；

（2）路由中元素或组件的渲染可定义element或者component；

（3）若有异常问题等情况，可用errorBoundary或errorElement来定义渲染；
