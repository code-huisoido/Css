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