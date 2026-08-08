---
title: Array Methods of JavaScript
published: 2026-08-08
description: "How to use array methods of js."
<!--image: "./cover.jpeg"-->
tags: ["JavaScript", "Learn"]
category: Technical Sharing
draft: false
---
# Array
## 特性
1. 下标访问
2. 可修改
3. arr.length 获取长度
4. Array 不支持 负数 下标访问, 即arr[-1], 但可以使用at(-1)访问
```JavaScript
let num = [1, 2, 3, 4]
alert(num.at(-1)) // return 4
```

## 基础方法

### 1. 数组
JavaScript中的Array类似于双端队列, 在首端/末端都可以添加/删除元素
> push/pop 的性能比 shift/unshift 好很多
```JavaScript
let num = ['apple', 'orange'];
// 末尾取出 pop
alert(num.pop) // return 'orange', num = ['apple']
// 末尾添加元素 push,可以指定多个
num.push('pear', 'banana') // num = ['apple', 'pear', 'banana']
// 首端取出 shift
alert(num.shift()) // return 'apple', num = ['pear', 'banana']
// 首端插入
num.unshift('apple') // num = ['apple', 'pear', 'banana']
```

### 2. 循环
```JavaScript
// 1. 
let num = ['apple', 'banana']
for(let i = 0; i < num.length;i++){
    console.log(num[i]);
}
// 2. for . of .
for(let n of num){
    console.log(n)  
}
```

### 3. toString()
```JavaScript
let num = [1, 2]
alert(num.toString()) // return "1,2"
```

### 4. Array 比较


### 5. 删除Array元素 - splice(start,deleteCount,elem1,...,elemN)
> 返回删除元素组成的数组
```JavaScript
let fruits = ['apple', 'banana', 'orange', 'pear'];
outFruits = splice(1,2) // 删除下标1开始的2个元素, 返回 ['banana', 'orange'], fruits = ['apple', 'pear']
replaceFruits = splice(1,1,'banana') // 删除下标1开始的1个元素, 并插入'banana', 返回 ['pear'], fruits = ['apple', 'banana']
```
当我们把deleteCount设为0时,`splice`就可以插入元素, 但不删除元素了
```JavaScript
addFruits = splice(0,0,'orange') // 在下标0处插入'orange', fruits = ['orange', 'apple', 'banana']
```

### 6. Array 切片 - slice(start, end)
```JavaScript
let fruits = ['apple', 'banana', 'orange', 'pear'];
let slicedFruits = fruits.slice(1, 3); // 返回 ['banana', 'orange'], fruits = ['apple'\
, 'banana', 'orange', 'pear']
```

### 7. 合并数组 arr.concat(arg1, arg2, ...)
```JavaScript
let num = [1, 2];
alert(num.concat([3,4])); // return [1, 2, 3, 4]
```

### 8. 数组中每个元素都执行函数 forEach
```JavaScript
let fruits = ['apple', 'banana', 'orange']
fruits.forEach((item, index, array) => {
    alert(`${item}在数组${array}中的下标为${index}`);
})
```

### 9. 查找元素 
#### indexOf(item, pos) includes(item, pos) 
与String相同，includes可以正确处理NaN；indexOf()返回下标, includes()返回bool值

#### find() - 返回对象 findIndex() - 返回下标
语法：let result = find(function(item, index, array){...})
```JavaScript
let fruits = [
   {id: 1, name: 'apple'},
   {id: 2, name: 'orange'},
]
let result = fruits.find(item => item.id == 1) // return {id: 1, name: 'apple'}
```

### 10. filter 筛选数组
语法：let result = arr.filter(function(item, index, array){...})
```JavaScript
let users = [
  {id: 1, name: "John"},
  {id: 2, name: "Pete"},
  {id: 3, name: "Mary"}
];

// 返回前两个用户的数组
let someUsers = users.filter(item => item.id < 3);
alert(someUsers.length); // 2
```

### 11. map - 将每个元素转换成字符串的长度
语法：let result = arr.map(function(item, index, array){...});最多可选择传入三个参数；
```JavaScript
let lengths = ["Bilbo", "Gandalf", "Nazgul"].map(item => item.length);
alert(lengths); // 5,7,6
```

### 12. sort(fn) - 排序
原地排序(in-place)；默认转换成字符串进行比较，设置fn可以改变排序方式
```JavaScript
let nums = [1, 15, 2];
nums.sort() // return [1, 15, 2]，因为默认按字符串排序
// 改变排序方式
function CompareNumber(a, b){
    if (a>b) return 1;
    if (a==b) return 0;
    if (a<b) return -1;
} // 返回正数代表大于，返回负数代表小于

nums.sort(CompareNumber) // return [1, 2, 15]

// 2. 更加简略的方式 - 箭头函数
nums.sort((a, b) => a-b)

// 3. 当比较字符串时，选择localeCompare
alert(['Österreich', 'Andorra', 'Vietnam'].sort((a, b) => a.localeCompare(b))) // return ["Andorra", "Vietnam", "Österreich"]
```

### 13. reverse() 逆置排序
```JavaScript
let arr = [1, 2, 3, 4, 5];
arr.reverse();

alert( arr ); // 5,4,3,2,1
```

### 14. 通过符号切分 - split
```JavaScript
let str = 'a,b,c,d,e';
let arr = str.split(","); // return ['a', 'b', 'c', 'd', 'e']
```

### 15. 符号拼接 - join
```JavaScript
let arr = ['a', 'b', 'c', 'd', 'e'];
let str = arr.join(","); // return 'a,b,c,d,e'
```

### 16.迭代查询 - reduce
语法：let value = arr.reduce(function(accumulator,item,index,array){...},[initial]);
> 其中initial为sum的accumulator默认值

```JavaScript
let arr = [1,2,3,4,5];
let result = arr.reduce((sum, current) => sum + current, 0);
alert(result)
```

| |sum|current|result|
|---|---|---|---|
|第一次调用|0|1|1|
|第二次调用|1|2|3|
|第三次调用|3|3|6|
|第四次调用|6|4|10|
|第五次调用|10|5|15|

### 17. Array.isArray(arr) 判断是否是数组
```JavaScript
let fruits = ['apple', 'banana', 'orange'];
alert(Array.isArray(fruits)); // return true
```

### 18. fill(value, start, end) 填充数据
> 左闭右开
```JavaScript
let arr = [1, 2, 3, 4, 5];
arr.fill(0, 2, 4); // return [1, 2, 0, 0, 5]
```

## 例题

### 1. 
写出函数 sumInput()，要求如下：

使用 prompt 向用户索要值，并存在数组中。
当用户输入了非数字、空字符串或者点击“取消”按钮的时候，问询结束。
计算并返回数组所有项之和。
P.S. 0 是有效的数字，不要因为是 0 就停止问询。

```JavaScript
sumInput = () =>{
    let num = [];
    let sum = 0;
    while(true){
        let n = prompt('请输入数字:');
        if(!isFinite(n) and n === NULL and n === '') break;
        sum += +n;
        num.push(+n);
    }
}
```
