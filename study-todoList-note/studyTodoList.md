## 整理 todoList demo

## 1、html 部分：

正常的格式：html-head-body（里面分成两部分：1、是用 container 装的页面 ui 部分；2、是引入 script.js）

用到了 form 标签来包了一个 input、ul（ul 这部分是用来显示添加到 input 后的 todolist 显示）

## 2、css 部分：

先是定义 body 部分的样式：给了 flex 布局（column、align 和 justify 都是给了居中对齐）、高度给了 100vh 可见、0 的外边距等；

跟着 html 里给的 class 给出不同的样式；

这里比较注意的是 todos 的样式：这里需要给完成后点击的样式为 todos li.completed{}

## 3、js 部分：

（1）通过 document.getElementById 来获取 html 里给出的 id 为（“”）

     const form = document.getElementById("form");
     const input = document.getElementById("input");
     const todosUL = document.getElementById("todos");

（2）监听 localStorage 里面是否有储存到 todos（是否有填写备忘录）

     const todos = JSON.parse(localStorage.getItem("todos"));

（3）判断上面的 todos 如果有储存的话，用 forEach 遍历一次 todos，把每一项 todo 都添加到 addtodo 里面去

     if (todos) {
       todos.forEach((todo) => addTodo(todo));
     }

（4）用 addEventListener 来监听 form 标签是否有"submit"提交事件发生，如果有，会执行下面的函数；

     form.addEventListener("submit", (e) => {
       e.preventDefault();//阻止默认提交

       addTodo();//addTodo函数调用
     });

（5）接下来写 addTodo 的函数：

     function addTodo(todo) {
       let todoText = input.value;//获取拿到input里输入的value

       if (todo) {
         todoText = todo.text;//判断todo参数如果有添加，将todo.text替换成新的todoText转化
       }

       if (todoText) {
         const todoEl = document.createElement("li");//这里的判断todotext存在的话，会在ul创建一个li
         if (todo && todo.completed) {
           todoEl.classList.add("completed");//如果todo存在并且存在点击完成的行为，把completed的样式给到完成的todo
         }

         todoEl.innerText = todoText;//把todoEl.innerText的备忘录事项添加为todoText

         //用addEventListener监听todoEl是否存在有点击click事件发生，如果有的话会执行下面函数
         todoEl.addEventListener("click", () => {
           todoEl.classList.toggle("completed");//会给备忘录事项“completed”的样式
           updateList();//执行updateList的函数更新备忘录list
         });

         //用addEventListener监听todoEl是否存在有右键点击事件发生，如果有的话会执行下面函数
         todoEl.addEventListener("contextmenu", (e) => {
           e.preventDefault();//调用这个函数来阻止浏览器的右键默认菜单

           todoEl.remove();//右键点击后会移除掉当前的todoEl
           updateLS();//调用更新备忘录list
         });

         todosUL.appendChild(todoEl);//把创建的todoEl放到todoUL里

         input.value = "";//同时会清空掉input的value

         updateList();//最后调用更新list
       }
     }

（6）更新 list 的函数：

     function updateList() {
       todosEl = document.querySelectorAll("li");//用querySelectorAll获取所有带有li元素

       const todos = [];

       //用forEach来遍历todosEl来把todo来用push添加到todos里去
       todosEl.forEach((todoEl) => {
         todos.push({
           text: todoEl.innerText,//获取文本todoEl.innerText
           completed: todoEl.classList.contains("completed"),
         });
       });

       localStorage.setItem("todos", JSON.stringify(todos));//用localStorage.setItem，把将todos 数组保存到浏览器的本地存储
     }

