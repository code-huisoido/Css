##css
> 整理来自：《写给大家看的CSS书》

###有用的链接
- http://validator.w3.org
- http://jigsaw.w3.org/css-validator
- www.stylinwithcss.com

###css secrets
- 放在css样式表的顶端
```css
* {margin:0; padding:0}
```
- 垂直的外边距折叠
```html
<!DOCTYPE html>
<html>
<head>
	<title>practice</title>
</head>
<style type="text/css">
	p {
		width : 400px;
		height : 50px;
		border : 1px solid #000;
		margin-top : 50px;
		margin-bottom : 30px;
		background-color : #CCC;
	}
</style>
<body>
<p>the first</p>
<p>the second</p>
<p>the three</p>
</body>
</html>
```

- 边框和内边距会增大盒子的宽度，解决办法是增加一个栏内元素
```html
<!-- 这样写会增大盒子的宽度 -->
<!DOCTYPE html>
<html>
<head>
	<title>practice</title>
</head>
<style type="text/css">
	* {
		margin:0;
		padding:0;
	}
	p {
		width : 400px;
		margin: 0 30px;
		padding:0 20px;
		border : #000 solid;
		border-width : 0 6px 0 6px;
		background-color : #CCC;
	}
</style>
<body>
<p>The element is 400 pixels wide</p>
</body>
</html>

<!-- 解决办法 -->
<!DOCTYPE html>
<html>
<head>
	<title>practice</title>
</head>
<style type="text/css">
	div#column {
		width : 170px;
	}
	div#column_inner {
		padding : 10px;
	}
</style>
<body>
<div id="column">
	<div id="column_inner">
		<h4>An h4 heading</h4>
		<p>The heading and this paragraph...</p>
	</div>
</div>
</body>
</html>
```

- 通过浮动构建分栏
```html
<!DOCTYPE html>
<html>
<head>
	<title>practice</title>
</head>
<style type="text/css">
	* {
		margin : 0;
		padding : 0;
	}
	img {
		float :left;
		width : 35px;
		margin : 0 4px 4px 0;
	}
	p {
		float : left;
		width : 200px;
	}
</style>
<body>
<img src="./logo.png" alt='picture'>
<p>Markdown 是一种方便记忆、书写的纯文本标记语言，用户可以使用这些标记符号以最小的输入代价生成极富表现力的文档：譬如您正在阅读的这份文档。它使用简单的符号标记不同的标题，分割不同的段落，粗体 或者 斜体 某些文字，更棒的是，它还可以...</p>
</body>
</html>
```

- 二栏布局
```html
<!DOCTYPE html>
<html>
<head>
	<title>2 column layout</title>
	<meta http-equiv="Content-Type" content="text/html" charset="utf-8" />
</head>
<link rel="stylesheet" type="text/css" href="./2_column_stable.css">
<body>
<div id="main_wrapper">
<div id="header">
	<div id="header_inner">
		<h1>The header area</h1>
	</div>
</div>

<div id="nav">
	<div id="nav_inner">
		<ul>
			<li><a href="#">Nav item 1</a></li>
			<li><a href="#">Nav item 2</a></li>
		</ul>
	</div>
</div>

<div id="content">
	<div id="content_inner">
		<h1>My text style sheet - h1 heading</h1>
		<p>A brief paragraph under this heading</p>
	</div>
</div>

<div id="footer">
	<div id="footer_inner">
		<p>This is the footer.</p>
	</div>
</div>
</div>
</body>
</html>
```
```css
/**
 * 2_column_stable.css
 */
body {
	text-align:center;
}

#main_wrapper {
	width:840px;
	margin-left:auto;
	margin-right:auto;
	text-align:left;
}

#header {

}

#nav {
	width:22%;
	float:left;
}

#content {
	width:78%;
	float:left;
	top:0px;
}

#footer {
	clear:both;
}

#header_inner, #nav_inner, #content_inner, #promo_inner {
	overflow:hidden;
}

#header_inner {
	padding:1em 2em;
}

#nav_inner {
	padding:1em .8em;
	border-right:3px solid #B33;	
}

#content_inner {
	padding:0 1em 1em 1.5em;
}

#footer_innner {
	padding:.5em 1em;
	text-align:center;
}
```

- 二栏流动式布局
```css
body {
	text-align:center;
}

#main_wrapper {
	margin-left:auto;
	margin-right:auto;
	text-align:left;
	max-width:960px;
	min-width:720px;
}

#header {

}

#nav {
	width:160px;
	float:left;
}

#content {
/*	width:78%;
	float:left;*/
	margin-left:160px;
}

#footer {
	clear:both;
}

#header_inner, #nav_inner, #content_inner, #promo_inner {
	overflow:hidden;
}

#header_inner {
	padding:1em 2em;
}

#nav_inner {
	padding:1em .8em;
	border-right:3px solid #B33;	
}

#content_inner {
	padding:0 1em 1em 1.5em;
}

#footer_innner {
	padding:.5em 1em;
	text-align:center;
}
```