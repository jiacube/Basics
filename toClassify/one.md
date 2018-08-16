### XMLHttpRequest.upload

XMLHttpRequest.upload方法返回一个XMLHttpRequestUpload对象，用来表示上传的进度。作为一个XMLHttpRequestEventTarget，可以通过对其绑定事件来追踪它的进度。

![xhrUpload](../images/xhrUpload.png)

### 字符流与字节流的区别

* 字节流操作的基本单元为字节；字符流操作的基本单元为Unicode码元。

* 字节流默认不使用缓冲区；字符流使用缓冲区。

* 字节流通常用于处理二进制文件，实际上它可以处理任意类型的数据，但它不支持直接写入或读取Unicode码元；字符流通常处理文本数据，它支持写入及读取Unicode码元。

### 贪婪匹配&非贪婪匹配

贪婪匹配: 正则表达式一般趋向于最长长度匹配。

非贪婪匹配: 匹配到结果就好、就少的匹配字符。

默认是贪婪模式;在量词后面直接加上一个问号?就是非贪婪模式。

### 物理分辨率 逻辑分辨率

物理分辨率是硬件所支持的，逻辑分辨率是软件可以达到的，互转的话乘以像素倍率。

### Charles | Fiddler

Charles是一个HTTP代理/HTTP监视器/反向代理，它允许开发人员查看他们的机器和Internet之间的所有HTTP和SSL/HTTPS通信，包括请求、响应和HTTP头(包括cookie和缓存信息)。

* 基本原理
将自己作为代理服务器、浏览器、手机app等客户端进行代理配置，配置成Charles监听的端口，客户端将请求发给Charles，Charles再将请求发送给真正服务器，结果返回时，由Charles转发给浏览器、手机等客户端。

### 简单数据结构

* 有序数据结构

    栈、队列、链表

    有序数据结构省空间(存储空间小)

* 无序数据结构

    集合、字典、散列表

    无序数据结构省时间(读取时间快)
### 复杂数据结构

* 树、堆

* 图

### 排序

* 快速排序

1.随机选择数组中的一个数A，以这个数为基准

2.其他数字跟这个数进行比较，比这个数小的放在其左边，大的放到其右边

3.经过一次循环之后，A左边为小于A的，右边为大于A的

4.这时候将左边和右边的数再递归上面的过程

````
const testArr = [67, 33, 12, 34, 11, 87, 54];
function quickSort(arr) {
    if (arr.length <= 1) {
        return arr;
    }
    let pivotIndex = Math.floor(arr.length / 2);
    let pivot = arr.splice(pivotIndex, 1)[0];
    let left = [];
    let right = [];
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] < pivot) {
            left.push(arr[i]);
        } else {
            right.push(arr[i]);
        }
    }
    return quickSort(left).concat([pivot], quickSort(right));
}
````