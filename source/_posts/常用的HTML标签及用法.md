---
title: 常用的HTML标签及用法
date: 2018-04-04 15:18:01
tags: HTML
---
常用的HTML标签总结
<!-- more -->
1. iframe

- 作用：嵌套页面

- 常用属性：
    - frameborder：取1时绘制边框，取0时去掉边框

    - name：嵌入 iframe 的名称。该名称可以用作 a 标签，form 标签的 target 属性值，或 input 标签和 button 标签的 formtaget 属性值
    - src： 嵌套页面的 URL 地址

- 用法：可将 a 标签的target属性设置成和 iframe 的 name 属性值相同，让 a 标签点击后的页面在 iframe 中打开

```html
<iframe name="xxx" src="#" frameborder="0"></iframe>
```
2. a 标签（HTTP请求 GET）
- 常用属性：
    - href:
        1. //qq.com(不指定协议时使用当前页面协议)
        2. #xxx
        3. javascaript:alert(1);
    - target: _self/_blank/_parent/_top，不设置时默认为_self,在当前页面刷新
    - download: 点击下载时使用
- 用法：当href值为#时，点击时页面锚点变成#，并且页面滚动到顶部，要想点击一个a标签什么也不发生可以使用javascript伪协议 javascript:;
```html
    <a href="#" target="_blank" download>
```

3. form （HTTP请求 POST）
- 作用：用来向web服务器提交信息
- 常用属性：
    - āction: 指定请求的路径
    - method: get/post
    - target: _self/_blank/_parent/_top

- 用法：form 中一定要有提交按钮，否则无法提交。GET方法，参数会被直接加到查询参数上，在URL上可见，POST方法，提交的数据在form data中，在开发者工具 network 选项中可以看到，form一般只用POST

```html
<form action="users" method="post" target="_blank">
    <label/>用户名：<input type="text" name="username"></label>
</form>
```
4. input/button
- 属性：
    1. type：button（普通按钮）/checkbox（复选框）/color（颜色）/date（日期控件）/email/file/hidden/image/month/number/password/radio（单选按钮）/range/reset（重置按钮）/search/search/submit（提交按钮）/tel/text/tel/text/time/url/tel/text/time/url/week
5. 下拉列表 selcet
```html
<select name="group">
    <option value="">-</option> 
    <option value="">第一组</option>
    <option value="">第二组</option>
    <option value="" disabled>第三组</option>
    <option value="" selected>第四组</option>
</select>
```
6. 多行文本 textarea

7. table
```html
<table>
<thead>
    <tr>
        <th><th>
    </tr>
</thead>
<tbody>
    <tr>
        <td></td>
    </tr>
</tbody>
<tfoot></tfoot>
</table>
```