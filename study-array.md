學習數組的常用方法：

1、push():

const arr = [1,2,3];
arr .push(4);
//在 arr 数组为 1，2，3 的后面加多一个 4，所以添加后的 arr 数组为[1,2,3,4]

2、pop():

const arr=[1,2,3];
const removeElement = arr.pop();
//用 pop 來移除數組最後一個元素，例如這裡移除的是 3，並且會返回數組[1,2]

3、shift():

const arr=[1,2,3];
const removeElement=arr.shift();
//用 shift 來移除數組的第一個元素，這裡移除的是 1，也同樣會返回數組元素值[2,3]

4、unshift():

const arr=[1,2,3];
arr.unshift(0);
//用 unshift 來給數組開頭添加一個或者多個元素，並且會返回新長度：[0,1,2,3]

5、concat():

const arrA=[1,2];
const arrB=[3,4];
const newArr=[1,2,3,4];
//用 concat 來將兩個或多個數組連結，並返回新數組 newArr；

6、splice():

const arr=[1,2,3,4,5];
arr.splice(2,1,`A`,`B`);
//用 splice 來在數組 arr 第 2 個元素開始刪除第一個元素，再加入[`A`,`B`],所以插入之後的數組為[1,2,A`,`B`,4,5]

7、indexOf() and lastIndex():用於查找數組中以某個元素的索引值：

const arr =[1,2,3,4,2]
const firstIndex = arr.indexOf(2);
//這裡返回的是 1；

const lastIndex =arr.lastIndex(2);
//這裡返回的是 4；

8、forEach()：

const arr=[1,2,3];
arr.forEach(item=>console.log(item));
//這裡用於遍歷數組裡的每個元素，並且執行提供的函數，這裡輸出為 1,2,3;

9、map():

const arr=[1,2,3];
const mappedArr = arr.map(item => item \* 2);
//這裡用於創建一個新數組，他的結果等於該數組中的每個元素都循環一次提供的函數後再返回其結果；

10、filter():

const arr =[1,2,3,4,5];
const filteredArr =arr.filter(item=>item>2);
//這裡的意思是用 filter 來篩選出 arr 裡所有大於 2 的元素
