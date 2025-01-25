## two-weeks studynote

通过这两周在本地练习的项目中，基本能熟悉了 js 在 DOM 操作、还有事件触发后的处理、还有状态的管理、以及通过 if、else 等判断语句来写出基本的逻辑；

总结：

## 1、通过 DOM 操作交互：

（1）获取 DOM 元素：
平常练习的项目中用的比较多的是：

document.getElementById（通括号内的 id 来获取 html 中对应的 id）、document.querySelector（通过括号内的元素来获取 html 中对应的 class）、document.querySelectorAll（选择 html 中的元素）

getElementsByClassName 来选择节点集合等

（2）创建、修改元素：

使用 document.createElement 动态生成 html 元素；

innerText、innerHTML 可以设置元素的属性和内容；

操作类名：classList.add、classList.remove、classList.toggle（动态调整样式）

（3）DOM 节点的插入、删除：

使用 appendChild、append 来插入节点；

以及调用 remove 方法来删除掉节点等；

## 2、事件触发后的监听和处理：

（1）事件的绑定、监听等：

使用 addEventListener 来监听事件（监听 click、submit、contextmenu 右键菜单栏触发）

使用 event.preventDefault 来阻止默认行为（项目中 input 得表单提交的刷新等）

（2）触发事件后的逻辑：

触发后，判断条件都符合的情况下，调用其他的函数；

同时修改动态 DOM、更新当前的状态等；

（3）使用 forEach 来遍历节点、每个元素上面的事件进行批量绑定、或者进行一些状态的操作；

## 3、状态管理 、本地存储等：

（1）状态的管理：

使用变量来进行保存状态，用来追踪当前选中元素的、状态；

定义数组或者对象来保存多个数据项的状态等；

（2）本地储存：localStorage：

localStorage.setItem：保存状态数据为 json 格式；

loaclStorage.getItem：获取状态数据，并且通过 JSON.parse 恢复为原始结果等

通过调用函数来更新、并且实现跟本地存储的数据同步更新；

## 4、判断逻辑、循环渲染操作：

判断：通过使用 if、else 的判断语句来对数据进行判断条件是否符合、数据是否存在等；

循环渲染操作：通过使用 forEach 来遍历数组、或者 NodeList，来执行批量操作，遍历中动态生成新的数组或者更新现有数组等；

## 5、动态样式、动画的控制、切换渲染等：

（1）动态样式的控制：
事件的触发后，通过添加、移除等类名动态来更改掉样式；，或者使用伪类（：：before）和 css 的变量（--line-border）来定义动态样式等；

（2）样式的切换：
将状态为 active、completed 绑定到元素的类名上，通过 CSS 来定义对应的样式；

## 6、逻辑的思维：

1、先分析项目的需求，对项目的 ui、样式、逻辑进行分解；

2、列出项目需要实现的功能点；

3、操作完成后需要更新的页面信息等；
