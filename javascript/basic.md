### call、apply和bind
改变某个函数运行时的上下文(context)，即改变函数体内部this的指向。

第一个参数都是this要指向的对象，即指定的上下文；利用后续参数传参。

bind返回绑定函数，便于稍后调用；call、apply是立即调用。

call和apply作用完全一样，接受参数方式的方式不一样。

````
//this是指定的上下文，call把函数顺序传递进去，apply是把参数放在数组里进行传递。
func.call(this, arg1, arg2);
func.apply(this, [arg1, arg2]);
````

### 存储方式
cookie、sessionStorage、localStorage、indexedDB

**相同点**：都保存在浏览器端，同源

**不同点**：
* 传递方式不同
* 数据大小不同
* 数据有效期不同
* 作用域不同

### 跨域
同源策略是浏览器的一个安全功能，不同源的客户端脚本在没有明确授权的情况下，不能读写对方资源。

若地址里面的协议、域名和端口号都相同则属于同源。

**跨域处理方式**：
* JSONP
* CORS
* Ngnix反向代理
* Node.js中间件代理跨域