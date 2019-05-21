---
title:   hexo next主题下开启emoji
date: 2019-05-04 17:00:00
comments: true
tags:
    - hexo
    - next
    - emoji
categories:
	- 技术
	- hexo
keywords:  [hexo,next,emoji]
---

![hexo](https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=3010013829,2497003625&fm=26&gp=0.jpg)

<!-- more -->

#### 写文章时会时不时的使用emoji表情，比如：:smile:

#### hexo默认的markdown渲染不支持GitHub emoji渲染的，所以只能换一个支持emoji的插件啦。

## 安装

#### 命令如下：

```cmd
npm uninstall hexo-renderer-marked --save
npm install hexo-renderer-markdown-it --save
npm install markdown-it-emoji --save
```

## 配置

#### 修改根目录下的 <code>_config.yml</code>,先查找一下<code>markdown</code>，有的话直接修改，没有的话，直接在文件最后添加即可。

```yaml
markdown:
  render:
    html: true
    xhtmlOut: false
    breaks: true
    linkify: true
    typographer: true
    quotes: '“”‘’'
  plugins:
    - markdown-it-footnote
    - markdown-it-sup
    - markdown-it-sub
    - markdown-it-abbr
    - markdown-it-emoji
  anchors:
    level: 2
    collisionSuffix: 'v'
    permalink: true
    permalinkClass: header-anchor
    permalinkSymbol: ¶
```

## 注意

#### <code>render:</code>下的<code>html</code>配置项，它的作用时控制markdown是否转义文章中的html标签，最好改为：<code>true</code>，改为：<code>false</code>的话，会导致<code>&lt;!--more--&gt;</code>无法被渲染。

## 使用方法

1. 在[GitHub emoji](https://www.webfx.com/tools/emoji-cheat-sheet/)直接点击表情复制代码，粘贴到需要的地方即可
2. 在[emoji](https://www.emojicopy.com/#emojicodes)中直接copy表情，粘贴到需要的地方即可。