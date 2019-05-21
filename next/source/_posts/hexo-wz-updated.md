---
title:   hexo next主题下显示文章更新时间
date: 2019-05-04 09:00:00
comments: true
tags:
    - hexo
    - next
    - updated
categories:
	- 技术
	- hexo
keywords:  [hexo,next,updated,更新时间]
---

![hexo](https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=3010013829,2497003625&fm=26&gp=0.jpg)

<!-- more -->

#### 一开始看了百度的结果，加了一堆代码，结果还不如意，我虽然是个菜鸟程序员，但是改代码还是比较在行的，我照着大佬的文章修改时，一不小心让我发现next主题的配置文件中竟然自带文章更新的配置，突然感觉自己好笨啊😂

#### 下面就开始修改吧：

##### 找到next主题的 <code>_config.yml</code>在里面查找 <code>update</code> 会找到一个 <code>updated_at</code> 的属性改为 <code>true</code> 即可。

##### 代码如下：

```yaml
post_meta:
  updated_at: true
```

