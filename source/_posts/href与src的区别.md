---
title: href与src的区别
---
###两者的定义
href (Hypertext Reference)指定网络资源的位置，从而在当前元素或者当前文档和由当前属性定义的需要的锚点或资源之间定义一个链接或者关系。当我们写下：
```
< link href="style.css" rel="stylesheet" / >
```
浏览器明白当前资源是一个样式表，页面解析不会暂停（由于浏览器需要样式规则去画或者渲染页面，渲染过程可能会被被暂停）。这与把css文件内容写在<style>标签里不相同，因此建议使用link标签而不是@import来吧样式表导入到html文档里。
src (Source)属性仅仅 嵌入当前资源到当前文档元素定义的位置。当浏览器找到
```
    <script src="script.js"></script>
```
在浏览器下载，编译，执行这个文件之前页面的加载和处理会被暂停。这个过程与把js文件放到<script>标签里类似。这也是建议把JS文件放到底部加载的原因。当然，img标签页与此类似。浏览器暂停加载直到提取和加载图像。

###两者区别
href和src是有区别的，而且是不能相互替换的。
(1)我们在可替换的元素*上使用src，然而把href用于在涉及的文档和外部资源之间建立一个链接或者关系。
(2)在浏览器下载，编译，执行src的值时，之前页面的加载和处理会被暂停；浏览器遇到href的值，页面解析不会暂停。

注，可替换元素：
>CSS 里，可替换元素（replaced element）的展现不是由CSS来控制的。这些元素是一类外观渲染独立于CSS的 外部对象。 典型的可替换元素有 < img>、 <object>、 <video> 和 表单元素，如<textarea>、 <input> 。 某些元素只在一些特殊情况下表现为可替换元素，例如 <audio> 和 <canvas> 。 通过 CSS content 属性来插入的对象 被称作 匿名可替换元素（anonymous replaced elements）。
