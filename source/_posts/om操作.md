title: Dom操作
author: Myongchon
tags: []
categories:
  - 前端
date: 2019-04-29 16:00:00
---
>javascript 原生方法对dom节点的操作具体包括：创建、添加、删除、替换、插入、复制、移动等

```
//查找节点
document.getElementById("id");// 通过id查找，返回唯一的节点
document.getElementsByClassName("class");// 通过class查找，返回值为nodeList类型
document.getElementsByTagName("div");// 通过标签名查找，返回值为nodeList类型

//创建节点
document.createDocumentFragment();//创建内存文档碎片
document.createElement();//创建元素
document.createTextNode();//创建文本节点
 
//添加节点
var ele = document.getElementById("my_div");
var oldEle = document.createElement("p");
var newEle=document.createElement("div");
ele.appendChild(oldEle);

//删除节点
ele.removeChild(oldEle);

//替换节点
ele.replaceChild(newEle,oldEle);

//插入节点
ele.insertBefore(oldEle,newEle);//在newEle之前插入 oldEle节点

//复制节点
var cEle = oldEle.cloneNode(true);//深度复制，复制节点下面所有的子节点
cEle = oldEle.cloneNode(false);//只复制当前节点，不复制子节点

//移动节点
var cloneEle = oldEle.cloneNode(true);//被移动的节点
document.removeChild(oldEle);//删除原节点
document.insertBefore(cloneEle,newEle);//插入到目标节点之前
```