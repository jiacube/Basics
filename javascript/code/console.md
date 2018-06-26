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
    setTimeout(function(i){
        console.log(i);
    }, i * 1000, i);
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

for (let i = 0; i < 5; i++) {
	setTimeout(function timer() {
		console.log(i); //每隔1s分别输出0, 1, 2, 3, 4
	}, i * 1000);
}
````

### Promise

* EX1

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

* EX2

````
new Promise(resolve => {
    console.log(1);
    resolve(3);
    Promise.resolve().then(() => console.log(4));
}).then(num => {
    console.log(num);
});
console.log(2);
//1 2 4 3
````

* EX3 all race

````
let p1 = new Promise((resolve) => {
    setTimeout(() => {
        console.log('1s');
        resolve(1);
    }, 1000);
});
let p10 = new Promise((resolve) => {
    setTimeout(() => {
        console.log('10s');
        resolve(10);
    }, 10000);
});
let p5 = new Promise((resolve) => {
    setTimeout(() => {
        console.log('5s');
        resolve(5);
    }, 5000);
});
Promise.all([p1, p10, p5]).then((res) => {
    console.log(res); //[1, 10, 5]
});
Promise.race([p1, p10, p5]).then((res) => {
    console.log(res); //1
});
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

* 方法1

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

* 方法2

````
var a = 1, b = 3;
console.log(a+++b);//4
````

#### 逗号运算符

````
var a = (function(){
    console.log('a');
    return 'a';
}, function(){
    console.log(1);
    return 1;
})();
console.log(typeof a); //number
````

#### ==运算符

解析：==运算符比较喜欢Number类型

````
//[]转换成Boolean
[] ? true : false;
//[]转换成Number，即0
[] == true ? true : false;
//[]转换成Number，即NaN
{} == true ? true : false;
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

### 函数

* 判断是否为函数

````
function isFunc(unknown){
    return typeof unknown === 'function';
}
````

### 严格模式

* 判断当前是否是严格模式

````
var strict = (function(){ return !this; }());
````

### 快速排序

````
function quickSort(arr) {
    if (arr.length <= 1) {
        return arr;
    }

    //1. 找基准(一般是以中间项为基准)
    var pivotIndex = Math.floor(arr.length / 2),
        pivot = arr.splice(pivotIndex, 1)[0],
        left = [],
        right = [];
    
    //遍历数组，把基准小的放在left，比基准大的放在right
    for (var i = 0; i < arr.length; i++) {
        if (arr[i] <= pivot) {
            left.push(arr[i]);
        } else {
            right.push(arr[i]);
        }
    }

    //递归
    return quickSort(left).concat([pivot], quickSort(right));
}
````

### map

````
//parseInt把传过来的索引值当成进制数来使用，从而返回了NaN
['1', '2', '3'].map(parseInt) //[1, NaN, NaN]
````

### this

````
const obj1 = {
    name: 'obj1',
    showName: function() {
        console.log(name);
    }
};
obj1.showName();

const obj2 = {
    name: 'obj2',
    showName: function() {
        console.log(this.name);
    }
};
obj2.showName();//obj2

const obj3 = {
    name: 'obj3',
    showName: function(name) {
        console.log(name);
    }
};
obj3.showName(this.name);
obj3.showName(name);

const obj4 = {
    name: 'obj4',
    showName: console.log(this.name)
};

const obj5 = {
    name: 'obj5',
    showName: console.log(name)
};
````

### 继承

````
function P(){}
P.prototype.a = 'a';
function C(){}
C.prototype = new P();
var obj1 = new C();
//第一种
obj1.__proto__.__proto__.a = 'c';
//第二种
obj1.constructor.prototype.a = 'c';
````

### toString

````
var a = {},
    b = {key: 'a'},
    c = {key: 'c'};
a[b] = '123';
a[c] = '456';
console.log(a); //[obejct Object]: "456"
````

  