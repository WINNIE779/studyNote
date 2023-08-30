## Responsive-web-desgin 
(自适应网页设计)-可自动根据屏幕像素大小，自动适应调整布局；


### 1、用法：在页面代码顶部加入viewport标签：

例如：

    <meta name="viewport" content="width=device-width, initial-scale=1"/>

viewport-指网页默认宽度；

width=device-width-指网页默认宽度等于屏幕宽度；

initial-scale=1-指原始缩放比例=1，即网页初始大小占屏幕面积的100%；



### 2、页面宽度


由于会根据屏幕大小变化调整布局，所以不能使用绝对宽度或绝对宽度的元素；


例如：

（1）CSS里不指定像素宽度，如：width：？ px；（这种为指定像素宽度）；

（2）只能指定百分比宽度或设置为自动默认宽度，如：width：？% 或 width：auto；


### 3、字体的相对大小

（1）如：

    body {
      font: nomal 100% Helvetica,Arial,sans-serif;
    }
    
指定义字体大小是页面默认大小的100%，即为16像素；


（2）如：

    h1 {font-size: 1.5em;}
    //1.5em=24px/16px;
    
指定义h1的字体大小是默认大小的1.5倍，1.5em为24px；


（3）如：

    h2{font-size:0.875em;}
    //0.875em*16px=14px;
    
指定义h2的字体大小为默认大小的0.875倍，即14像素（14px/16px=0.875em);

### 4、流动布局（fluid grid)

指可定义每个框浮动的位置及大小变化；
（float优点：当宽度较小放不下两个元素时，后面的元素会自动滚动到前面元素的下方，不会在同一水平方向overflow；）

例如：
（1）

    .image{
        float:right;
        width:70%;
        }
指定义.image里的内容在屏幕宽度变化后浮动在页面的右边，里面的内容则占页面默认大小的70%；

（2）

    .text{
        float:left;
        width:30%;
        }
指定义.text里的内容在屏幕宽度变化后浮动在页面的左边，里面的内容则占页面默认大小的30%；




