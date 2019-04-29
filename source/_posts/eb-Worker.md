title: Web Worker
author: Myongchon
tags: []
categories: []
date: 2019-04-29 14:52:00
---
HTML5引进了 Web Worker，可让JS在后台运行，执行耗时长的任务，而不影响主页面代码的执行。<br>
1.定义：Web Worker 是HTML5标准的一部分，允许一段JavaScript程序运行在主线程之外的另外一个线程中。Web Worker 规范中定义了两类工作线程，分别是专用线程Dedicated Worker和共享线程 Shared Worker，其中，Dedicated Worker只能为一个页面所使用，而Shared Worker可以被多个页面所共享，本文以前者为例。
