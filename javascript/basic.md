### call、apply和bind
改变某个函数运行时的上下文(context)，即改变函数体内部this的指向。
第一个参数都是this要指向的对象，即指定的上下文；利用后续参数传参。
bind返回绑定函数，便于稍后调用；call、apply是立即调用。
call和apply作用完全一样，接受参数方式的方式不一样。
    func.call(this, arg1, arg2);
    func.apply(this, [arg1, arg2]);
    this是指定的上下文，call把函数顺序传递进去，apply是把参数放在数组里进行传递。