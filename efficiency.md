### 雅虎军规

* 尽量减少HTTP请求数

合并文件   CSS Sprites

* 使用CDN(内容分发内容)

判断用户来源就近访问服务器取得所需的内容。

* 添加Expire/Cache-Control头

浏览器会用缓存来减少HTTP请求数加快页面加载的时间，如果页面头部加一个很长的过期时间，浏览器就会一直缓存在页面里的元素。

* 启用Gzip压缩

* 将CSS放在页面最上面

* 将script放在页面最下面

* 避免在CSS中使用Expressions

页面显示、缩放、滚动乃至移动鼠标

* 将JavaScipt和CSS都放到外部文件中

通过权衡内置代码带来的HTTP请求减少与使用外部文件进行缓存带来的好处的折中点。

* 减少DNS查询

* 压缩JavaScript、CSS、字体和图片等

* 避免重定向

* 移除重复的脚本

重复调用的代码浏览器并不会识别忽略，而是会再次运算一遍，从而删除重复脚本很重要。

* 配置实体标签(ETag)

实体标签是web服务器和浏览器用于判断缓存中的内容和服务器中的原始内容是否匹配的一种机制，使用ETag减少web应用的负载。

* 使Ajax缓存

Ajax是实时响应，通过使用Ajax更好地提高效果。

* 图片懒加载

* 减少DOM元素数量

* 减少DOM操作

* 使用CSS Sprite

* 避免图片src为空

* 尽量减少iframe使用

* 多域名分发划分内容到不同域名

