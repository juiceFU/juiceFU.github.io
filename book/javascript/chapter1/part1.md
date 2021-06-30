## 一、script标签

### 1.script元素

**①参数：**

- [async]：表示应该立即下载脚本，但不应妨碍页面的其他操作，比如下载其他资源或等待加载其他脚本。==只对外部脚本文件有效==；

- [charset]：因为一般浏览器忽略他，所以很少人用；

- [defer]：表示脚本可以延迟到文档完全被解析和显示之后在执行，只对外部脚本文件有用；

- [src]：表示包含要执行代码的外部文件;

- [type]：内容类型(也称为MIME类型)，text/javascript  ： 默认值；


**②不可以在js中间出现</script>标签，如需要，可以通过转义符\来写，例如：**

```
<script>
alert("<\/script>");
</script>
```
**③在解析外部javascript代码时，包括下载文件，页面的处理也会暂停;**

**④XHTML可以省略</script>，HTML不可以省略;**

**⑤js扩展名不是必须的，所以可以通过服务器来生成js代码,但是要确定浏览器能返回正确的MIME类型（type）;**

**⑥下面的例子中，只会加载外部文件，标签中间的代码会被忽略**
```
<script src="1.js">alert("这个弹窗会被忽略")</script>
```
**⑦src可以加载外部域的文件，与img类似，所以加载外部域文件的时候要小心；**
**⑧只要不出现defer（延迟加载）和async（立即加载脚本），浏览器就会按照出现得先后顺序加载js，加载完一个再加载下一个；**

### 2.标签出现的位置

- 传统：出现在header中
    
    会导致浏览器加载页面的时候出现迟缓
- 现代web应用：放在body后

    加快页面呈现速度
    
### 3.延迟脚本（defer）
> 只适用外部文件

> 用途是：脚本在执行时不会影响页面的构造，脚本会被延迟到整个页面都被解析完毕后再运行，这个属性是告诉浏览器，==立即下载，延迟执行==


```
<script src="1.js" defer="defer"></script>
<script src="2.js" defer="defer"></script>
```
猜猜看？延迟后先执行那个？为什么

按h5规范，脚本按照出现的顺序执行，1.js会先于2.js执行，but，现实中不一定，所以一个页面中最好只放一个延迟脚本。

h5规定是会先于DomContentLoaded事件触发之前执行，现实是不一定会先于DomContentLoaded事件触发之前执行；

注意：有可能不兼容，所以把延迟脚本放在页面底部执行时最佳的选择

### 4.异步脚本（async）

> 只适用于外部文件

> 用途是：不让页面等待脚本的下载和执行，异步的页面其他内容，所以异步脚本要在加载的时候修改DOM，告诉浏览器，立即下载

```
<script async src="1.js"></script>
<script async src="1.js"></script>
```
猜猜看？谁先执行？

答案是：不能确定，2.js可能先于1.js执行，so，要保证两个脚本不是互相依赖的关系，

异步脚本一定会在页面的load事件之前加载，可能会在DomContentLoaded事件触发之前或之后执行；

注意：可能不兼容；

### 5.XHTML中的用法

XHTML比HTML严格，小于号<就是错的，会出现语法错误，因为会把他解析为一个新标签，所以要使用\&lt;（HTML实体）代替，这种写不好理解，所以用下面的方式:

```
<script>
//<![CDATA[
    alert("CData在xhtml中表示特殊区域")
//]]
</script>
```

CData在xhtml中表示特殊区域，有的浏览器不兼容所以不兼容的就把它注释掉，这样就都能用了

### 6.使用外部文件的优点

- 可维护性
- 可缓存性

    如果有两个页面同时使用一个文件，那这个文件只需要下载一遍
- 适应未来

    HTML和XHTML调用js的方式是不一样的
    
### 7.文档模式

- 混杂模式

  浏览器的默认模式
- 标准模式
    
```
<!--HTML4 严格型-->
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML4.01//EN" "http://www.w3.org/TR/html14/strict.dtd">

<!--XHTML1.0 严格型-->
<!DOCTYPE HTML PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<!--h5-->
<!DOCTYPE html>
```
、、、还有过渡型、框架集型

### 8.<noscript>标签
在浏览器不支持script标签的时候用这个，支持javascript的浏览器永远都不会看到它，比如：

```
<noscript>
    本页面需要浏览器支持（启用）JavaScript
</noscript>
```

