## JavaScript-数组（Array)
数组是可以使用数字为索引（0开始的整数）来操作元素，而数组中的元素可以是多种数据、函数、或是数组等，如果数组存放数组称为二维数组。

### 创建数组

1.使用字面量创建（最简易）

例：let arr=[ ];

在括号内加入需要的数字，多个的话需要用逗号隔开，不加入数值则为创建空数组；


2.使用构造函数创建 

语法：
     
     let arr=new Array( );

     let arr=Array( );
在括号内加入数值，多个的话需要用逗号隔开，不加入数值则为创建空数组，有多个参数表示数组中的元素内容。


### 数组中常见方法：

一、数组类型

1.Array.isArray() 

用于判断是否为数组；

语法：

    布尔值=Array.isArray();//括号中加入需要检测的数组；

二、数组转换为字符串，有三种方式：

1.toString( )

语法：

    字符串=数组.toString();
例:

    const result=[1,2]toString();得到的结果：result为字符串`1,2` .

2.String（ ）

语法：

    字符串=String（数组）；
例：
   
    const result=String(1,2,3);得到的结果：result为字符串`1,2,3`.

3.join（ ）

语法：

    新的字符串=原数组.join();
例：

    const arr=[`a`,`b`];
    const result1= arr.join()；括号内可加入连接符，不加的话则按逗号（，）作为连接符；
    const result2= arr.join(`-`)；
得到的结果：

         result1为a，b
         result2为a-b；

4.split（ ）

是字符串的方法，不是数组方法；

语法：
     
     数组=str.split(分隔符)；

5.Array.from()

用于将伪数组转换为真数组；伪数组是含length属性的对象或可迭代的对象，相当于字符串/元素；

语法：

    array=Array.from(arrayLike);
例：

    const name=`xiao`;
    console.log(Array.from(name));（console 打印）
    打印数组结果为：["x","i","a","o"] 

6.Array.of（ ）

用于创建数组；new Array()和Array.of()区在于若参数只有一个时，new Array（）表示数组的长度，Array.of（）则表示数组中的内容；

语法：

    Array.of(value1,value2,value3);
例：

    const arr=Array.of(1,`ab`,true);
    console.log(arr);
打印数组结果为：[1，“ab”，true];







