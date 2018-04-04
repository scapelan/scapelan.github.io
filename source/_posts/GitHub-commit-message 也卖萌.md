---
title: GitHub commit message 也卖萌
date: 2017-12-09 19:37:12
tags: GitHub
---
一篇GayHub卖萌指南
<!-- more -->
最近在最大同性交友平台 ~~GitHub~~ GayHub上看到有些项目的commit message是这样的

{% asset_img emoji.png %}

是不是比只有枯燥的文字要萌很多~

查了一下发现GitHub早在2014年就支持emoji了，不仅issue，wiki可以使用emoji，甚至git commit message也可以使用emoji了，而且不光可以卖萌，在commit信息里添加emoji也让commit信息更加一目了然

用法也是非常的简单，只要在需要emoji的地方添加相应的emoji代码即可，比如

```
# 项目初次提交代码
git commit -m ":tada: Initialize Repo"
```

并且每一个emoji都有特定的含义，可以查看这个页面 https://gitmoji.carloscuesta.me/

还有一个包含更多emoji的页面 https://www.webpagefx.com/tools/emoji-cheat-sheet/

如果嫌每次都要去复制emoji代码太麻烦，可以使用[gitmoji-cli](https://github.com/carloscuesta/gitmoji-cli)工具
```
#安装gitmoji-cli工具
npm i -g gitmoji-cli
```
安装好之后，可以根据提示交互式选择emoji