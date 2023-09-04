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


