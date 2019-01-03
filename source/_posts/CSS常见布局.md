---
title: CSS常见布局
date: 2018-04-08 12:57:47
tags: CSS
---
这里所说的常见布局是指利用float，position，margin，padding等属性来进行的布局，不包括flex布局和grid布局。
<!-- more -->
## 单列布局
没什么好说的
```html
<!-- html -->
<div class="body">
    <div class="header"></div>
    <div class="container"></div>
    <div class="footer"></div>
</div>

<! -- css -->
.body{
    max-width: 1200px;
    margin: 0 auto;
}
```
## 左右布局
```html
<!-- html -->
<div class="body">
    <div class="left"></div>
    <div class="right"></div>
</div>
```
### float + overflow
将左框设置为float: left，右框设置overflow: hidden
```html
<!-- html -->
<div class="body">
        <div class="left">111</div>
        <div class="right">222</div>
</div>

<! -- css -->
.left{
    float: left;
    width: 200px;
    margin-right: 10px;
}
.right{    
    overflow: hidden;
}
```
### float + margin
将左框脱离文档流，设置右框的margin-left为左框的宽度
```html
<!-- css -->
.body{
    max-width: 1200px;
    margin: 0 auto;
}

.left{
    width: 200px;
    float: left;
}

.right{
    margin-left: 200px;
}
```
### position + margin
原理和使用float类似，只是将左框用position: absolute固定，右框设margin-left
```html
/* css */
.body{
    max-width: 1200px;
    margin: 0 auto;
}

.left{
    position: absolute;
    top: 0;
    left: 0;
    width: 200px;
}

.right{
    margin-left: 200px;
}
```
## 左中右布局
### 左中两列定宽，右列自适应
左中两栏设置float: left、width、margin-right，再设置右栏overflow: hidden
```html
<!-- html -->
<div class="body">
    <div class="left">1</div>
    <div class="center">2</div>
    <div class="right">3</div>
</div>

<!-- css -->
.left, .center{
    float: left;
    width: 100px;
    margin-right: 20px;
}
 .right{
    overflow: hidden;
}
```
### 两边定宽，中间自适应
#### 圣杯布局
布局步骤：
1、三列内容都设置向左浮动。
2、设置center宽度为100%，设置两侧栏的宽度。
3、设置left左边距为负100%，设置right左边距为负的自身宽度。
4、设置container的padding值给左右两块内容留空间。
5、设置left、right为相对定位，左侧的left属性值为负自身宽度，右侧的right属性值为负自身宽度。
```html
<!-- html -->
<div class="container">
    <div class="center"></div>
    <div class="left"></div>
    <div class="right"></div>
</div>

<!-- css -->
.container{
    padding: 0 150px;
}

.center{
    float: left;
    width: 100%;
}

.left, .right{
    position: relative;
    float: left;
    width: 150px;
}

.left{
    left: -150px;
    margin-left: -100%;
}

.right{
    right: -150px;
    margin-left: -150px;
}
```
#### 双飞翼布局
- 双飞翼布局的思路和圣杯布局类似，区别在于圣杯使用padding放侧栏，双飞翼使用margin放侧栏，解决了圣杯布局main的最小宽度不能小于左侧栏的缺点。
- 双飞翼布局不用设置相对布局，以及对应的left和right值。
- 通过引入相对布局，可以实现三栏布局的各种组合，例如对右侧栏设置position: relative; left: 150px; ,可以实现left+right+content的布局。
```html
<div class="container">
        <div class="content">1</div>
</div>
<div class="left">2</div>
<div class="right">3</div>

.container, .left, .right{
    float: left;
}

.container{
    width: 100%;
}

.left{
    width: 150px;
    margin-left: -100%;
}

.right{
    width: 150px;
    margin-left: -150px;
}

.content{
    margin: 0 150px;
}
```