# HTML 语言简介

## 概述

HTML 是网页使用的语言，定义了网页的结构和内容。浏览器访问网站，其实就是从服务器下载 HTML 代码，然后渲染出网页。

HTML 的全名是“超文本标记语言”（HyperText Markup Language），上个世纪90年代由欧洲核子研究中心的物理学家蒂姆·伯纳斯-李（Tim Berners-Lee）发明。它的最大特点就是支持超链接，可以跳转到其他网页，从而构成了整个互联网。

浏览器的网页开发，涉及三种技术：HTML、CSS 和 JavaScript。HTML 语言定义网页的结构和内容，CSS 样式表定义网页的样式，JavaScript 语言定义网页与用户的互动行为。本教程只介绍 HTML 语言。

1999年，HTML 4.01 版发布，成为第一个广泛接受的 HTML 标准版本。2014年，HTML 5 发布，是目前正在使用的版本。

下面就是一个简单网页的 HTML 代码。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>网页标题</title>
</head>
<body>
  <p>Hello World</p>
</body>
</html>
```

上面这段代码保存成文件，文件名可以取为`hello.html`，然后在浏览器加载这个本地文件，应该就能看到“Hello World”。

## 基本概念

### 标签

HTML 代码由许许多多不同的标签（tag）构成。

```html
<title>网页标题</title>
```

上面代码中，`<title>`和`</title>`就是一对标签，“网页标题”就是这个标签的内容。

标签用来告诉浏览器，如何处理这段代码。标签的内容就是浏览器所要渲染的、展示在网页上的内容。

标签放在一对尖括号里面，比如`<title>`。大多数标签都是成对出现的，分成开始标签和结束标签，结束标签在标签名之前加斜杠，比如`</title>`。但是，也有一些标签不是成对使用，而是只有开始标签，没有结束标签，比如上面的`<meta>`标签。

```html
<meta charset="utf-8">
```

对于单个使用的标签，由于没有结束标签，当然也就不存在标签内容。它们主要用来提示浏览器，做一些特别处理。

标签可以嵌套。

```html
<div><p>hello world</p></div>
```

上面代码中，`<div>`标签内部包含了一个`<p>`标签。

嵌套时，必须保证正确的闭合顺序，不能跨层嵌套，否则会出现意想不到的渲染结果。

```html
<div><p>hello world</div></p>
```

上面代码就是错误的嵌套，闭合顺序不正确。

标签名是大小写不敏感，比如`<title>`和`<TITLE>`是同一个标签。不过，一般习惯都是使用小写。

另外，HTML 语言忽略缩进和换行。也就是说，下面的写法与上面的写法效果是一样的。

```html
<title>
  网页标题
</title>
```

进一步说，整个网页的 HTML 代码完全可以写成一行，浏览器照样解析，结果完全一样。有时，正式发布网页之前，开发者会把源码压缩成一行，以减少传输的字节数。网页内容的缩进和换行要靠 CSS 样式和特定的标签来实现。

### 元素

有的标签是实义标签，也就是说，标签有对应的实体，即对应 HTML 网页的元素（element）。比如，`<p>`标签对应网页的`p`元素。

嵌套的标签就构成了网页元素的层级关系。

```html
<div><p>hello world</p></div>
```

上面代码中，`div`元素内部包含了一个`p`元素。这时，上层元素称为“父元素”，下层元素称为“子元素”，即`div`是`p`的父元素，`p`是`div`的子元素。

元素分成块级元素（block）和行内元素（inline）两种。块级元素默认占据一个独立的区域，在网页上会自动另起一行，占据 100% 的宽度。

```html
<p>hello</p>
<p>world</p>
```

上面代码中，`p`元素是块级元素，因此浏览器会将内容分成两行显示。

行内元素默认与其他元素在同一行，不占据一个单独的区域。通常用来为某些文字指定特别的样式。

```html
<span>hello</span>
<span>world</span>
```

上面代码中，`span`元素是行内元素，因此浏览器会将内容放在一行显示。

### 属性

属性（attribute）是标签的额外信息，使用空格与标签名和其他属性分隔。

```html
<img src="demo.jpg" width="500">
```

上面代码中，`<img>`标签有两个属性：`src`和`width`。

属性可以用等号指定属性值，比如上例的`demo.jpg`就是`src`的属性值。属性值一般放在双引号里面，这不是必需的，但推荐总是使用双引号。

注意，属性名是大小写不敏感的，`onclick`和`onClick`是同一个属性。

## 网页的基本标签

符合语法标准的网页，应该满足下面的基本结构。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title></title>
</head>
<body>
</body>
</html>
```

不管多么复杂的网页，都是从上面这个基本结构衍生出来的。

注意，HTML 代码的缩进和换行，对于浏览器来说都不重要。上面的例子完全可以写成一行，渲染结果不变。上面这样写，只是为了提高可读性。

下面介绍，这个基本结构里面的每一个标签。

### `<!doctype>`

网页的第一个标签通常是`<!doctype>`，用来表示文档类型，告诉浏览器如何解析网页。

一般来说，只要像下面这样，简单声明成`html`即可。浏览器就会按照 HTML5 的规则，处理这个网页文件。

```html
<!doctype html>
```

有时，该标签采用完全大写的形式，以便区别于正常的 HTML 标签。因为`<!doctype>`本质上不是标签，而是一个针对浏览器的处理命令。

```html
<!DOCTYPE html>
```

### `<html>`

`<html>`标签是网页的顶层容器，也称为根元素（root element），其他元素都是它的子元素。一个网页只能有一个`<html>`标签。

该标签的`lang`属性，表示网页内容默认的语言（详见《元素属性》一章）。

```html
<html lang="en">
```

上面代码表示，网页的语言是英语。

### `<head>`

`<head>`标签是一个容器标签，表示网页的元信息，用于放置网页的头部内容。它与页面的渲染不是直接相关，而是为渲染做准备。

```html
<!doctype html>
<html>
  <head>
    <title>Document title</title>
  </head>
</html>
```

`<head>`是`<html>`的第一个子元素。如果网页不包含`<head>`，浏览器会自动创建一个。

### `<meta>`

`<meta>`标签用于指定网页的一些元数据，必须放在`<head>`里面。一个`<meta>`标签就是一项元数据，网页可以有多个`<meta>`。

`<meta>`的`name`属性表示元数据的名字，`content`属性表示元数据的值。

```html
<head>
  <meta name="description" content="HTML 语言入门">
  <meta name="keywords" content="HTML,教程">
  <meta name="author" content="张三">
</head>
```

上面代码包含了三个元数据：`description`是网页内容的描述，`keywords`是网页内容的关键字，`author`是网页作者。

其他的元数据还有很多种，都涉及到浏览器内部工作机制，或者特定的使用场景。这里就不一一介绍了，放在后文的相关内容里介绍。

`<meta>`还有一个`charset`属性，指定网页内容的编码方式，该属性非常重要。如果设置得不正确，浏览器无法正确解码，可能会出现乱码。

```html
<meta charset="utf-8">
```

上面代码声明，网页为`utf-8`编码。虽然可以使用其他的编码方式，但 UTF-8 实际已经足够使用。

注意，声明的编码方式，应该与网页实际的编码方式一致，即声明了`utf-8`，网页就应该使用 UTF-8 编码保存。

### `<title>`

`<title>`标签用于指定网页的标题，会显示在浏览器窗口的标题栏。

```html
<head>
  <title>网页标题</title>
</head>
```

搜索引擎也是采用这个标签的内容，显示每一项搜索结果的标题。并且，`<title>`标签对于网页在搜索引擎的排序，有很大的影响，应该精心安排，反映网页最重要的主题。

`<title>`标签的内部，不能再放置其他标签，只能放置无格式的纯文本。

### `<body>`

`<body>`标签是一个容器标签，用于放置网页的主体内容。浏览器显示的页面内容，就是在这里指定。它是`<html>`的第二个子元素，紧跟在`<head>`后面。

```html
<html>
  <head>
    <title>网页标题</title>
  </head>
  <body>
    <p>hello world</p>
  </body>
</html>
```

## 空格和换行

对于空格，HTML 语言有自己的处理规则。标签内容里面的多个连续空格（包含制表符`\t`），会被浏览器合并成一个。

```html
<p>hello      world</p>
```

上面代码中，`hello`与`world`之间有多个连续空格，浏览器会将它们合并成一个。网页渲染的结果是，`hello`与`world`之间只有一个空格。

浏览器还会将文本里面的换行符（`\n`）和回车符（`\r`），替换成空格。

```html
<p>hello



world
</p>
```

上面代码中，`hello`与`world`之间有多个换行，浏览器会将它们替换成空格，然后再将多个空格合并成一个。网页渲染的结果是，`hello`与`world`之间有一个空格。

这意味着，HTML 源码里面的换行，不会产生换行效果。

## 注释

HTML 代码可以包含注释，浏览器会自动忽略注释。注释以`<!--`开头，以`-->`结尾，下面就是一个注释的例子。

```html
<!-- 这是一个注释 -->
```

注释可以是多行的，并且内部的 HTML 都不再生效了。

```html
<!--
  <p>hello world</p>
-->
```

上面代码是一个注释的区块，内部的代码都是无效的，浏览器不会解析，更不会渲染它们。

注释有助于理解代码的含义。
