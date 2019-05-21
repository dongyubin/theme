---
title: web前端：css学习的第一天
date: 2019-05-15 17:00:00
comments: true
tags:
    - web
    - web前端
    - html
    - css
categories:
	- 教程
	- web
keywords:  [web,web前端,htm,cssl]
---

![css](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1557909174865&di=41b717c775a533a8e90c1a182c2be5b9&imgtype=0&src=http%3A%2F%2Fs11.51cto.com%2Fimages%2F201508%2Fa88cc46043b39fc3a1d05645ab645f4df590b0.jpg)

<!-- more -->

### CSS基本语法

#### 语法

```html
<head>
  <style type="text/css">
    选择器（即修饰对象）{
      对象的属性1:属性值1;
      对象的属性2:属性值2;
    }
  </style>
</head>
```

#### 选择器分类

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>标签选择器</title>
    <style type="text/css">
        /*内嵌>id>类>标签*/

        /*id选择器*/
        #yellow{
            color: #FF0;
        }
        /*类选择器*/
        .blue{
            /*相同的样式类选择器比标签选择器权重高*/
            color: blue;
        }
        /*标签选择器*/
        li{
            color: red;
            /*同种样式在相同的选择器的情况下，下面的属性比上面的属性权重高*/
            color: #F39;
        }

    </style>
    <link type="text/css" rel="stylesheet" href="css/style.css"/>
</head>
<body>
    <ul>
        <li class="blue" id="yellow" style="color: black">列表1</li>
        <li>列表2</li>
        <li class="gray">列表3</li>
        <li class="blue">列表4</li>
        <li>列表5</li>
    </ul>
</body>
</html>
```

##### 在css/style.css

```css
.gray{
    color: gray;
}
```

### 字体样式

#### 字体、字号：

##### 粗细：font-weight

##### 大小：font-size

##### 字体：font-family

#### 行距、对齐等：

##### 行高：line-height

##### 对齐：text-align

##### 字符间距：letter-spacing

##### 文本修饰：text-decoration

##### 空白处理：while-space

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>字体样式</title>
    <style type="text/css">
        .div{
            font-weight: 600;/*加粗600及600以上或者blod；不加粗500及500以下*/
            font-size: 32px;
            font-family: "Andale Mono" ;
            line-height: 100px;/*行高就是行级元素文本在设定的高度中上下对齐居中*/
            background: red;
            text-align: center;/*水平方向的对齐方式：适用于行级元素或者文本*/
            letter-spacing: 10px;
            text-decoration: underline;
        }

        .box{
            font-size: 12px;
        }

        .box_li1{
            text-decoration: underline;
            letter-spacing: 10px;
        }

        .box_li2{
            font-size: 15px;
            color: red;
        }

        li{
            line-height: 40px;
        }
    </style>
</head>
<body>
<div class="div">大家好<a href="#">123</a> </div>
<h1 style="font-weight: 500; white-space: nowrap; width: 100px; background: #960;">我的网页</h1>
    <ul class="box">
        <li class="box_li1">圣爱大厦</li>
        <li class="box_li2">是手机卡号发</li>
        <li>即打算离开</li>
        <li>阿驱蚊器</li>
        <li class="box_li2">娃儿去</li>
    </ul>
</body>
</html>
```

### 背景

#### 背景属性

##### 背景色：background-color

|             值              |      示例      |
| :-------------------------: | :------------: |
|         color_name          |      red       |
|         hex_number          |    \#FF3399    |
|         rgb_number          | rgb(250,0,250) |
|      transparent(透明)      |  transparent   |
| inherit（从父元素继承属性） |    inherit     |

##### 背景图片：background-image

##### 背景重复：background-repeat

##### 背景定位：background-position

##### 背景关联：background-attachment

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>背景色</title>
    <style type="text/css">
        .box{
            width: 400px;
            height: 500px;
            background-color: red;
        }

        h1{
            background-color: transparent;
        }

        h2{
            background-color: #FF3399;
        }
        p{
            background-color: rgb(250,0,250);
        }

        .no2{
            background-color: gray;
            padding: 20px;
        }


    </style>
</head>
<body>
<div class="box">
    <h1>标题2</h1>
    <h2>标题2</h2>
    <p>这是段落</p>
    <p class="no2">带有内边距的段落</p>
</div>

</body>
</html>
```

