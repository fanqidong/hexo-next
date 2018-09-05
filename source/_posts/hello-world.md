---
title: Hello World
categories: hexo
tags: hexo
reward: fasle
---
<!-- HTML方式: 直接在 Markdown 文件中编写 HTML 来调用 -->
<!-- 其中 class="blockquote-center" 是必须的 -->
<blockquote class="blockquote-center">blah blah blah</blockquote>

<!-- 标签 方式，要求版本在0.4.5或以上 -->
{% centerquote %}![tool-editor](http://img0.utuku.china.com/440x0/news/20180712/a7fd615b-4af1-4202-af3f-bad4422e180b.jpg){% endcenterquote %}


<!-- 标签别名 -->
{% cq %} blah blah blah {% endcq %}
<!-- More -->
{% note primary %} content (md partial supported) {% endnote %}

## Quick Start

### Create a new post

``` bash
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)
