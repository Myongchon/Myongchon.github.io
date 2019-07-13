---
layout: '@media'
title: screen网页布局的自适应
date: 2019-05-06 17:46:53
tags:
---
**media feature -- 媒体部分特性**

width -- 定义输出设备中的页面可见区域宽度
height -- 定义输出设备中的页面可见区域高度
device-width -- 定义输出设备的屏幕可见宽度
device-height -- 定义输出设备的屏幕可见高度
orientation -- 定义'height'是否大于或等于'width'。portrait代表是（竖屏），landscape代表否（横屏）
aspect-ratio -- 定义width与height的比率，可以设置min/max
device-aspect-ratio -- 定义device-width与device-height的比率。可以设置min/max。如常见的显示器比率：4/3, 16/9, 16/10
resolution -- 定义设备的分辨率。可以设置min/max。如：96dpi, 300dpi, 118dpcm
color -- 定义每一组输出设备的彩色原件个数。如果不是彩色设备，则值等于0。可以设置min/max
media query 常用方法



- 排他 （exclusive） 为确保在某一个条件下只有一个样式表生效，将查询条件严格划分，如下面：
```
@media (max-width: 400px) {
    html {
        background: red;
    }
}

@media (min-width: 401px) and (max-width: 800px) {
    html {
        background: green;
    }
}

@media (min-width: 801px) {
    html {
        background: blue;
    }
}
```



- 覆盖（overriding） 可以对元素设置相同优先级，使用样式顺序，通过覆盖，避免排他
```
@media (min-width: 400px) {
    html {
        background: red;
    }
}

@media (min-width: 600px) {
    html {
        background: green;
    }
}

@media (min-width: 800px) {
    html {
        background: blue;
    }
}
```



- 无线端优先（Mobile first） 默认样式假设为移动设备宽度，然后通过min-width控制扩展样式
```
html {
    background: red;
}

@media (min-width: 600px) {
    html {
        background: green;
    }
}
```



- PC优先（desktop first） 默认以宽屏进行样式设置，通过max-width控制样式覆盖
```
html {
    background: red;
}

@media (max-width: 600px) {
    html {
        background: green;
    }
}
```
