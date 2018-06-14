### 判断是否为数组

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

### 数组去重

参考链接：https://www.jb51.net/article/118657.htm

* 方法1 ES6的set

````
function distinct(arr) {
    if (Array.isArray(arr)) {
        return Array.from(new Set(arr));
        //return [...new Set(arr)];
    }
}
````

* 方法2 利用对象的属性不能相同的特点进行去重

````
function distinct(arr) {
    var i, len = arr.length, obj = {}, res = [];

    if (Object.prototype.toString.call(arr) === '[object Array]') {
        for (i = 0; i < len; i++) {
            if (!obj[arr[i]]) {
                obj[arr[i]] = 1;
                res.push(arr[i]);
            }
        }
    }

    return res;
}
````

* 方法3 indexOf

* 方法4 排序去重

* 方法5

双层循环，外层循环元素，内层循环比较值：值相同就删去这个值

注意点：删除元素之后，需要将数组的长度也减1

* 方法6

双层循环，外层循环元素，内层循环比较值：如果有相同的值则跳过，不相同则放入数组

### 平铺数组

* 方法1

````
function flattenDeep(arr){
    return arr.join(',').split(',');
}
````

* 方法2 递归

````
const deepFlatten = arr => [].concat(...arr.map(v => (Array.isArray(v) ? deepFlatten(v) : v)));
````






