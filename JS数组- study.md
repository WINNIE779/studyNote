数组

1.includes（ ）

用于判断数组中是否含了指定元素，如果是会返回true，否的话会返回false。

语法：

      布尔值=arr.includes(加入想要查找的元素，[position]);

2.find（ ）

用于找出第一个满足指定条件的true元素，并就此停止查找，不会继续往下查找；若无满足相关条件的，则会返回undefined；

语法：

     const itemResult=arr.find((currentItem,currentIndex,currentArray)=>{
         reurn true;
      });//指item、Index、Array在数组里当前的元素下查找，符合条件则返回true；

3.findIndex（ ）

用于查找第一个指定条件返回true的元素的索引，并立即停止遍历；如果没找到，则返回-1.

语法：

     const indexResult= arr.findIndex((currentItem,currentIndex,currentArray)=>{
         return true;
     });//语法用了跟find（）一样的方法。

例：

    let arr=[0,1,2,3,4]；
    
    let result=arr.findIndex((item,index)=>{
        return item >3；
    });
    console.log（result）；//在以上arr=0，1，2，3，4中条件满足第一个大于3的值，打印结果是4。

4.every（ ）

用于对数组每一项运行回调函数，如果返回都是true，every就返回true；如果其中一项有则返回了false，停止遍历，此方法返回false。
every（ ）方法的返回值是布尔值，参数时回调函数。

语法：

      const boolResult=arr.every((currentItem,currentIndex,currentArray)=>{
            return true;
      });


      
      



      
