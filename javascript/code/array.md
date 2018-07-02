### 数组的方法

#### join()

作用: 可以把一个数组的所有元素都转换成字符串，然后再把它们连接起来。

参数: 分隔符；无参数，默认,分隔

是否修改原始值: 否

返回值: 字符串

````
var beforeArr = [1, 2, 3],
    returnStr = beforeArr.join();
console.log(beforeArr); //[1, 2, 3]
console.log(returnStr); //1,2,3
````

#### reverse()

作用: 颠倒数组元素的顺序并返回颠倒后的数组。

参数: 无参数

是否修改原始值: 是 

返回值: 颠倒后的数组

````
var beforeArr = [1, 2, 3],
    afterArr = beforeArr.reverse();
console.log(beforeArr); //[3, 2, 1]
console.log(afterArr); //[3, 2, 1]
````

#### sort()

* 作用: 在原数组上对数组元素进行排序，返回排序后的数组。

* 参数: 比较函数

如果比较函数第一个参数应该位于第二个参数之前，那么比较函数将返回一个小于0的数。如果比较函数第一个参数应该位于第二个参数之后，那么比较函数就会返回一个大于0的数。如果两个参数相等，那么比较函数将返回0。

* 是否修改原始值: 是

* 返回值: 排序后的数组

````
var beforeArr = ['Abc', 'abc', 111, '1bc'];
console.log(beforeArr.sort()); //[111, "1bc", "Abc", "abc"]
console.log(beforeArr); //[111, "1bc", "Abc", "abc"]
````

#### concat()

作用: 创建并返回一个数组

参数: 需要添加的元素，如果有些参数是数组，那么它将被展开

注意: concat()并不能递归展开一个元素为数组的数组

是否修改原始值: 否

返回值: 合并的数组

````
var arr = [1, 2],
    addEl1 = ['b', 'c'],
    addEl2 = [3, [4, 5]],
    addEl3 = 'd';
console.log(arr.concat(addEl1, addEl2, addEl3)); //[1, 2, "b", "c", 3, [4, 5], "d"]
console.log(arr); //[1, 2]
````

#### splice()

作用: 插入或删除数组元素的通用方法

参数

    第一个参数: 要插入或删除的元素在数组中的位置
    第二个参数: 要从数组删除的元素个数，被省略则将删除从开始元素到数组结尾处的所有元素
    后续参数: 从第一个参数指定的位置处开始插入的元素

是否修改原始值: 是

返回值: 删除的元素数组

````
var arr = [1, 2, 3, 4, 5];
console.log(arr.splice(1, 2, 'a')); //[2, 3]
console.log(arr); //[1, "a", 4, 5]
````

#### slice()

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






