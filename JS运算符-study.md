## 运算符（operater）

(1)  
使用 + 的运算符把文本字符串连接，如：

    const a ="Apple";
    const b ="hello";
    const c = a + b;

（2）
复合赋值运算符，可以把（1）写成：

    let a1 ="Apple";
    a1 +="hello";
    //等价于：
    let a2="Apple";
    a2=a2 + "hello";

(3)
当做判断true or false时，比较运算符，如：

1、=== 全等 
例如：
 
    5 === 1 + 5 // 显示fals；
    5 === 2 + 3 // 则显示true；
    2 === '2' // 也显示false；因数字与字符串不相等；

2、！== 不相等
例如：

    5 !== 2 + 4 //显示true；
    5 !== 2 + 3 // 则显示false；
    2 !== '2' // 显示true；数字与字符串不相等；

3、&& 和的运算符

当作判断A和B两者是否都为true或false时，可用&&连接同时作判断，如：


    A && B === true：false //可同时作判断

4、|| 或的运算符

当判断A或B是否有一个是true时，返回true，否则false，如：

    A || B ? true : false 

5、？？ 空值合并的操作符

？？空值合并操作符是一个逻辑操作符，
当左侧操作数为null或undefined时，返回的事其右侧的操作数，反之则返回左侧操作数，如：
 
     A ?? B   
     //当A为 null 或者 undefined 时，返回 B，反之则返回A；


    
