---
title: jQuery选择器
date: 2019-05-14 22:22:56
tags:
categories:
  - 前端
---
1.jQuery 元素选择器

>id选择器:  `$("#test");`
class选择器: `$(".test");`
节点选择器: `$("p");`

2.jQuery 属性选择器
>`$("div[id]"); `选择所有含有id属性的div元素
`$("input[name='like']"); `选择所有的name属性等于'like'的input元素
`$("input[name!='like']") ;`选择所有的name属性不等于'like'的input元素
`$("input[name^='like']"); `选择所有的name属性以'like'开头的input元素 ​
`$("input[name*='like']");`选择所有的name属性包含'like'的input元素

3.jQuery CSS 选择器
$("p").css("background-color","red");

4.jQuery 表单选择器
>`$(":input")` 选择所有的表单输入元素，包括input, textarea, select 和 button 
`$(":text")` 选择所有的text input元素 
`$(":password")` 选择所有的password input元素 
`$(":radio")` 选择所有的radio input元素 
`$(":checkbox")` 选择所有的checkbox input元素 
`$(":submit")` 选择所有的submit input元素 
`$(":image")` 选择所有的image input元素 
`$(":reset")` 选择所有的reset input元素 
`$(":button")` 选择所有的button input元素 
`$(":file")` 选择所有的file input元素 
`$(":hidden")` 选择所有类型为hidden的input元素或表单的隐藏域 
<br>
**备注:**
`$(":input")`和`$("input")`的区别

`$("input")`是节点选择器,表示选择所有input节点.
`$(":input")`是表单选择器,表示选择所有表单元素,包括textarea,select.

*jquery选择器空格,大于号,加号和波浪号的区别(类似CSS选择器)*
1. 空格：`$('parent childchild')`表示获取parent下的所有的childchild节点（所有后代）。
2. 大于号：`$('parent>child')`表示获取parent下的所有child的第一代后代。
3. 加号：`$('pre+nextbrother')`表示获得pre节点的下一个兄弟节点，相当于next()方法
4. 波浪号：`$('pre~brother')`表示获取pre节点的后面的所有兄弟节点，相当于nextAll()方法。
