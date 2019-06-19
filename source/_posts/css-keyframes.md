---
title: css @keyframes
date: 2019-06-19 11:28:13
tags: css
catepories: 前端
---

## 定义和用法

通过 @keyframes 规则，您能够创建动画。

创建动画的原理是，将一套 CSS 样式逐渐变化为另一套样式。

在动画过程中，您能够多次改变这套 CSS 样式。

以百分比来规定改变发生的时间，或者通过关键词 "from" 和 "to"，等价于 0% 和 100%。

0% 是动画的开始时间，100% 动画的结束时间。

为了获得最佳的浏览器支持，您应该始终定义 0% 和 100% 选择器。

**注释：**请使用动画属性来控制动画的外观，同时将动画与选择器绑定。

## 浏览器支持

|  IE  |     Firefox     |       Chrome       |       Safari       |     Opera     |
| :--: | :-------------: | :----------------: | :----------------: | :-----------: |
|      | @-moz-keyframes | @-webkit-keyframes | @-webkit-keyframes | @-o-keyframes |

目前浏览器都不支持 @keyframes 规则。

Firefox 支持替代的 @-moz-keyframes 规则。

Opera 支持替代的 @-o-keyframes 规则。

Safari 和 Chrome 支持替代的 @-webkit-keyframes 规则。

## 语法<!--more-->

```
@keyframes animationname {keyframes-selector {css-styles;}}
```

| 值                   | 描述                                                         |
| :------------------- | :----------------------------------------------------------- |
| *animationname*      | 必需。定义动画的名称。                                       |
| *keyframes-selector* | 必需。动画时长的百分比。合法的值：0-100%from（与 0% 相同）to（与 100% 相同） |
| *css-styles*         | 必需。一个或多个合法的 CSS 样式属性。                        |

## 亲自试一试 - 实例

### demo.html

```
<!DOCTYPE html>
<html >
<head>
	<meta charset="utf-8">
	<title>css loading animation</title>
	<link rel="stylesheet" type="text/css" href="style.css">
</head>
<body>
	<div class="loading">
		<span>loading</span>
	</div>
</body>
</html>
```

### style.css

```css
body{
	margin:0;
	padding: 0;
	background: #34495e;
	height: 100vh;
	display: flex;
	align-items: center;
	justify-content: center;
	font-family: "montsereat",sans-serif;
}

.loading{
	width: 200px;
	height: 200px;
	/*background:red;*/
	box-sizing: border-box;
	border-radius: 50%;
	border-top:10px solid #e74c3c;
	position: relative;
	animation: a1 2s linear infinite;
}

.loading::before,.loading::after{
	content: '';
	width: 200px;
	height: 200px;
	/*background: red;*/
	position: absolute;
	left: 0;
	top: -10px;
	box-sizing: border-box;
	border-radius: 50%;
}

.loading::before{
	border-top:10px solid #e67e22;
	transform: rotate(120deg);
}

.loading::after{
	border-top:10px solid #3498db;
	transform: rotate(240deg);
}

.loading span{
	position: absolute;
	width: 200px;
	height: 200px;
	color: #fff;
	text-align: center;
	line-height: 200px;
	animation: a2 2s linear infinite;
}

@-webkit-keyframes  a1{ 	/*chrome*/
	to{
		transform: rotate(360deg);
	}
}

@-webkit-keyframes  a2{		/*chrome*/
	to{
		transform: rotate(-360deg);
	}
}
```

