---
title: JavaScript数组方法总结
date: 2017-12-03 20:47:55
tags: JavaScript
---
JavaScript数组方法总结
<!-- more -->
# 数组的方法
1. join()
2. reverse()
3. sort()
4. concat()
5. slice()
6. splice()
7. push()和pop()\
8. unshift()和shift()
9. toString()和toLocaleString()
10. forEach()
11. map()
12. filter()
13. every()和some()
14. reduce()和reduceRight
15. indexOf()和lastIndexOf()

# 1. join()
join()方法将数组中所有元素转化成字符串并连接在一起，参数可指定分隔符，如参数为空，默认逗号为分隔符
```js
var a = [1, 2, 3];
a.join(); //=>"1,2,3"

```
# 2. reverse()
reverse()方法返回原数组逆序排列后的数组
```js
var a = [1, 2, 3];
a.reverse(); //a是[3,2,1]
```
# 3.sort()
返回原数组排序后的数组，不加参数时按照ASCII表顺序排列，按其他顺序排列时必须传入一个比较函数
```js
var a = [33, 4, 1111, 222];
a.sort(); //=> [1111, 222, 33, 4]
//从小到大排
a.sort(function(a,b) {
    return a-b;
})
//从小到大，另一种方法
a.sort(function(){
   if (x < y){
      return -1;
   }
   if (x > y){
       return 1;
   }
   return 0;
})
```

# 4.concat 
返回一个新数组，新数组的元素包括原始数组的元素和concat()的参数，如果参数为数组，连接的数组的元素，但concat()不会递归扁平化数组的数组
```js
var a = [1, 2, 3];
a.concat(4, 5); //返回[1,2,3,4,5]
a.concat([4, 5]); //返回[1,2,3,4,5];
a.concat([4,[5,[6,7]]); //返回[1,2,3,4,5,[6, 7]]
```

# 5.slice()
返回数组的一个片段，返回的数组从第一个参数指定的位置到第二个参数-1的位置
```js
var a = [1,2,3,4,5];
a.slice(0,3); //返回[1,2,3]
a.slice(3); //返回[4,5]
a.slice(1,-1) //返回[2,3，4] 参数-1时表示倒数第一个元素
a.slice(-3,-2) //返回[3]
```

# 6.splice()
返回被删除的数组，第一个元素指定删除和插入的起始位置，第二个参数指定了要删除元素的个数，后面的参数指定需要插入到数组中的元素
```js
var a = [1,2,3,4,5,6,7,8];
a.splice(4); //返回[5,6,7,8],a是[1,2,3,4]
a.splice(1,2); //返回[2,3],a是[1,4]
```
```js
var a = [1,2,3,4,5];
a.splice(2,0,'a','b'); //返回的是[],a是[1,2,'a','b',3,4,5]
a.splice(2,2,[1,2],3); //返回的是['a','b'],a是[1,2,[1,2],3,3,4,5]
```

# 7.push()和pop()
push()在数组尾部添加一个或多个元素，并返回数组新的长度
pop()删除数组最后一个元素，并返回删除的值
```js
var stack = [];
stack.push(1,2); //stack:[1,2] 返回2
stack.pop(); //stack:[1] 返回2
stack.push(3); //stack:[1,3] 返回2
```

# 8.unshift()和shift()
unshift()在数组的头部增加一个或多个元素，并返回数组新的长度
shift()删除数组第一个元素并将其返回
```js
var a = [1];
a.unshift(22); //a:[22,1] 返回2
a.shift(); //a:[1] 返回22
```

# 9.toString()和toLocaleString()
toString()将每个元素转化为字符串,输出用逗号分隔的字符串列表
```js
[1,2,3].toString() //生成'1,2,3'
["a","b","c"].toString() //生成'a,b,c'
[1,[2,'c']].toString() //生成'1,2,c'
```
toLocaleString()是toString()方法的本地化版本，它调用元素的toLocaleString()将每个元素转化为字符串

# 10.forEach()
从头至尾遍历数组，为每个元素调用指定的函数
```js
var data = [1,2,3,4,5];
var sum = 0;
data.forEach(function(value){
    sum += value;
});
sum   //=>15
//每个数组元素的值自加1
data.forEach(function(v,i,a){
    a[i] = v + 1;
})
```
# 11.map()
将数组的每个元素传递给指定的函数，并返回一个包含该函数返回值的数组
```js
a = [1,2,3];
b = a.map(function(x){
    return x*x;
}); //b是[1,4,9]
```

# 12.filter()
filter()方法返回的数组是调用的数组的一个子集，传递进的函数用来逻辑判定，如果返回值为true或能转化为true的值，那么将传递给判定函数的这个元素放入这个子集
```js
a = [5,4,3,2,1];
smallvalues = a.filter(function(x){
    return x<3
}); //[2,1]
everyother = a.filter(function(x,i){
    return i%2 == 0;
}); //[5,3,1]
```

# 13.every()和some()
every()和some()方法是数组的逻辑判定，every()是当所有元素调用判定函数都返回true，它才返回true，some()是只要有一个元素调用判定函数返回true，它就返回true
```js
a = [1,2,3,4,5];
a.every(function(x){
    return x < 10;
}); //true: 所有的值都小于10
a.some(function(x){
    return x%2===0;
}; //true: a含有偶数
```
# 14.reduce()和reduceRight()
reduce()方法将数组中的每一个元素按照回调函数的运算方式进行运算，生成单个值，第一个参数为回调函数，第二个参数为初始值，初始值省略时，使用数组的第一个元素作为初始值。reduceRight()从右到左化简数组。
```js
var a = [1,2,3,4,5];
var sum = a.reduce(function(x,y){
    return x+y
}, 0) //数组求和
```
# 15.indexOf()和lastIndexOf()
搜索整个数组中有给定值的元素，并返回找到的第一个元素的索引，如果没找到就返回-1，indexOf()从头至尾搜索，lastIndexOf()则反向搜索，第一个参数是需要搜索的值，第二个参数（可选）表示开始搜索的位置的索引。
```js
//在数组中查找所有出现的x，并返回一个包含匹配索引的数组
function findall(a, x){
    var results = [];
    len = a.length;
    pos = 0;
    while(pos < len){
        pos = a.indexOf(x,pos);
        if (pos === -1) break;
        results.push(pos);
        pos = pos + 1;
    }
    return results;
}
```




