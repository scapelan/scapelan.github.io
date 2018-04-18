---
title: CSS布局
date: 2018-04-04 18:35:55
tags: CSS
---
CSS布局方案总结
<!-- more -->
# CSS布局
## 两栏布局

1. 子框均左浮，父框清除浮动
```html
<style>
        .clearfix::after{
            content: '';
            display: block;
            clear: both;
        }
        .container{
            border: 2px solid yellow;
        }
        main{
            float: left;
            border: 1px solid red;
        }
        aside{
            float: left;
            border: 1px solid green;                        
        }
</style>

<div class="container clearfix">
        <main>main</main>
        <aside>aside</aside>
    </div>
</div>
```
2. 一栏定宽，一栏自适应

这种定宽+自适应的布局经常在一些内容型网站中看到，比如知乎、简书，定宽栏可以用来加目录或者导航，


