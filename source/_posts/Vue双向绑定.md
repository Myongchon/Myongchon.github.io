---
title: Vue双向绑定
date: 2019-05-30 19:26:23
tags:
categories:
  - 前端
---
####双向绑定特点
数据的双向绑定是vue实现的一大功能。
使用v-model指令，实现视图和数据的双向绑定。
所谓双向绑定，指的是vue实例中的data与其渲染的DOM元素的内容保持一致，无论谁被改变，另一方会相<br>应的更新为相同的数据。这是通过设置属性访问器实现的。
**v-model主要用在表单的input输入框，完成视图和数据的双向绑定。**
**v-model只能用在<input>、<select>、<textarea>这些表单元素上。**
```
<!DOCTYPE html>
<html>
<head></head>
<body>
  	<div id="app">
    	<input type="text" v-model="message">
    	<p>{{message}}</p>
  	</div>
  	<script>
    	var app = new Vue({
      		el: '#app',
      		data: {
        		message: ''
      		}
    	});
  	</script>
</body>
</html>
```
用Vue.js中的v-model来添加双向绑定：
```
<input v-model="xxx">
```
其实上面的代码等价于下面的：
```
<input :value="xxx" @input="xxx = $event.target.value">
```
也就是说：

>双向绑定 = 单向绑定 + UI事件监听

- 双向绑定与单向绑定有优缺点

1. 单向绑定：使得数据流也是单向的，对于复杂应用来说这是实施统一的状态管理（如redux）的前提。
2. 双向绑定：在一些需要`实时反应用户输入的场合`会非常方便（比如`多级联动菜单`）。但通常认为复<br>杂应用中这种便利比不上引入状态管理带来的优势。因为我们不知道状态什么时候发生改变，是谁造成的改变，数据变更也不会通知我们
注意，Vue 虽然通过 v-model 支持双向绑定，但是如果引入了类似redux的vuex，就无法同时使用 v-model
