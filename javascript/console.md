### 定时器
````
for (var i = 0; i < 5; i++) {
    console.log(i); //0 1 2 3 4
}

for (var i = 0; i < 5; i++) {
    setTimeout(function(){
        console.log(i); //每隔1s输出5
    }, 1000 * i);
}

for (var i = 0; i < 5; i++) {
    (function(i) {
        setTimeout(function(){
            console.log(i); //每隔1s分别输出0，1，2，3，4
        }, 1000 * i);
    })(i);
}

for (var i = 0; i < 5; i++) {
    (function(i){
        setTimeout(function(){
            console.log(i); //同时输出5个undefined
        }, 1000 * i);
    })();
}

for (var i = 0; i < 5; i++) {
    (function(){
        setTimeout(function(){
            console.log(i); //每隔1s输出5
        }, 1000 * i);
    })(i);
}

for (var i = 0; i < 5; i++) {
    setTimeout((function(){
        console.log(i); //每隔1s分别输出0，1，2，3，4
    })(i), 1000 * i);
}

for (var i = 0; i < 5; i++) {
    setTimeout((function(){
        console.log(i); //每隔1s分别输出0，1，2，3，4
    })(), 1000 * i);
}
````
### Promise
````
setTimeout(function(){
    console.log(1);
}, 0);

new Promise(function executor(resolve){
    console.log(2);
    for(var i = 0; i < 5; i++){
        resolve();
        i++;
        console.log(3);
    }
}).then(function(){
    console.log(4);
});

console.log(5);
//输出2 3个3 5 4 1
````
### 字符串
* slice、substring和substr的区别
````
var str = 'Hello World!'
/*
slice
    两个参数：起始位置和结束位置（不包括结束位置）
    当接收的参数是负数时，slice会将字符串的长度和对应的负数相加，结果作为参数
*/
console.log(str.slice(4, 7));//o W
/*
substring
    两个参数：起始位置和结束位置（不包括结束位置）
    substring是以两个参数中较小一个作为起始位置，较大的参数作为结束位置substring将负参数转换为0
*/
console.log(str.substring(7, -6));//Hello W
/*
substr
    两个参数：起始位置和所要返回的字符串长度
    将负的第一个参数加上字符串的长度，第二个参数转换为0
*/
console.log(str.substr(-6, 7));//World!
````
### 表达式和运算符
#### 赋值表达式
````
var num1 = 4,
    num2 = 5;
console.log((num1 = num2) == 0);//num1=num2返回5，所以结果为false
````
#### 一元运算符
````
var arr1 = [1, 2, 3],
    i1 = 0;
arr1[i1++] *= 2;
console.log(arr1, i1);//[2,2,3] 1

var arr2 = [1, 2, 3],
    i2 = 0;
arr2[i2++] = arr2[i2++] * 2;
console.log(arr2, i2);//[4,2,3] 2
````
#### eval
````
/*
    当通过别名调用的时候，
    eval会将其字符串当成顶层的全局代码来执行。
*/
function testEval(){
    var newEval = eval,
        x = 5;
    newEval('var x = 3');
    conole.log('inner', x);//inner 5
}
testEval();
console.log('outer', x);//outer 3
````
### 语句
#### 循环
````
[2, 3, 4, 5, 6].forEach(console.log);
/* 输出
    2 0 [2, 3, 4, 5, 6]
    3 1 [2, 3, 4, 5, 6]
    4 2 [2, 3, 4, 5, 6]
    5 3 [2, 3, 4, 5, 6]
    6 4 [2, 3, 4, 5, 6]
*/
````
### 对象
* bind
````
var bindFun = function(){
    console.log(this.x);
}
var foo = {
    x: 3
};
var sed = {
    x: 4
};
console.log(bindFun.bind(foo).bind(sed)());//3
````
### 数组
* 判断是否为数组
````
function isArray(unknown){
    return Object.prototype.toString.call(unknown) === '[object Array]';
}

function isArrayByType(unknown){
    return typeof unknown;
}

//用instanceof和constructor判断的变量，必须在当前页面声明
function isArrayByInstance(unknown){
    return unknown instanceof Array;
}

function isArrayByConstructor(unknown){
    return unknown.constructor === Array;
    //return unknown.__proto__.constructor === Array;
}
````
### 函数
* 判断是否为函数
````
function isFunc(unknown){
    return typeof unknown === 'function';
}
````


  