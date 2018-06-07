### Node多进程
Node.js提供了cluster模块和child_process模块创建子进程，从而提高CPU的利用率。
### Vue双向绑定
通过Object.defineProperty实现
````
<div id="app">
    <input type="text" id="txt"/>
    <p id="show-txt"></p>
</div>
<script>
    var obj = {};
    Object.defineProperty(obj, 'txt', {
        get: function() {
            return obj;
        },
        set: function(newValue) {
            document.getElementById('txt').value = newValue;
            document.getElementById('show-txt').innerHTML = newValue;
        }
    });
    document.addEventListener('keyup', function(e){
        obj.txt = e.target.value;
    });
</script>
````
### requestAnimationFrame
window.requestAnimationFrame()方法希望执行动画并请求浏览器在下一次重绘之前调用指定的函数来更新动画。该方法使用一个回调函数，这个回调函数会在浏览器重绘之前调用。
* 优化并行的动画动作，更合理地重新排列动作序列，并把能够合并的动作放在一个渲染周期内完成，从而呈现出更流畅的动画效果。
* 解决毫秒的不精确性
* 避免过度渲染