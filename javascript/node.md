### Node多进程

Node.js提供了cluster模块和child_process模块创建子进程，从而提高CPU的利用率。

### 事件循环(Event Loop)

#### 浏览器端

执行栈 事件队列(Task Queue)

不同的任务源会被分配到不同的Task队列中，任务

宏任务：setInterval()   setTimeout()

微任务：new Promise()   new MutaionObsever()

当前的执行栈执行完毕时会立刻先处理所有微任务队列中的事件，
然后再去宏任务队列中取出一个事件，同一个事件循环中，
微任务永远在宏任务之前执行。

#### Node