# URL

## 简介

URL 是“统一资源定位符”（Uniform Resource Locator）的首字母缩写，中文译为“网址”，表示各种资源的互联网地址。下面就是一个典型的 URL。

```html
https://www.example.com/path/index.html
```

所谓资源，可以简单理解成各种各样可以访问的文件，比如，网页文件、图像文件、媒体文件、脚本文件等等。只有知道了它们的 URL，才可能在互联网上获取它们。

只要资源可以通过网络访问，就必然存在 URL，即一个 URL 对应一个资源。但是，同一个资源可能对应多个 URL。

URL 是互联网的基础。互联网之所以称为“互联”，就是因为网页文件可以包含指向其他网页的 URL，这称为“链接”（link）。用户只要轻轻一点击，就可以从一个 URL 跳转到另一个 URL，前往不同的网站。

## 组成部分

URL 由多个部分组成，但是不一定同时具有每个部分。为了讲解，下面是一个比较复杂的 URL。

```html
https://www.example.com:80/path/to/myfile.html?key1=value1&key2=value2#anchor
```

我们看看，这个 URL 的各个部分。

### 协议

协议（scheme）指的是，浏览器请求服务器资源的方法。上例就是`https://`的部分，表示使用 HTTPS 协议。

互联网支持多种协议，必须指明网址使用哪一种协议，默认是 HTTP 协议。也就是说，如果省略协议，直接在浏览器地址栏输入`www.example.com`，那么浏览器默认会访问`http://www.example.com`。HTTPS 是 HTTP 的加密版本，出于安全考虑，越来越多的网站使用这个协议。

HTTP 和 HTTPS 的协议名称后面，紧跟着一个冒号和两个斜杠（`//:`）。其他协议不一定如此，邮件地址协议`mailto:`，协议名后面只有一个冒号，比如`mailto:foo@example.com`。

### 主机

主机（host）是资源所在的网站名或服务器的名字，又称为域名。上例的主机是`www.example.com`。

有些主机没有域名，只有 IP 地址，比如`192.168.2.15`。这种情况常常出现在局域网。

### 端口

同一个域名下面可能同时包含多种网站，它们之间通过端口（port）区分。“端口”就是一个整数，可以简单理解成，访问者告诉服务器，想要访问哪一个网站。默认端口是80，如果省略了这个参数，服务器就会返回80端口的网站。

端口参数紧跟在域名后面，两者之间使用冒号分隔，比如`www.example.com:80`。

### 路径

路径（path）是资源在网站文件系统的位置。比如，`/path/index.html`这个路径，指向网站的`/path`子目录下面的网页文件`index.html`。

互联网的早期，路径是真实存在的物理位置。不过，现在由于服务器可以模拟这些位置，所以路径只是虚拟位置。

路径可能只包含目录，不包含文件名，比如`/path/`，甚至结尾的斜杠都可以省略。这时，服务器通常会默认跳转到该目录里面的`index.html`文件（即等同于请求`/foo/index.html`），但也可能有其他的处理方法（比如列出目录里面的所有文件），这取决于服务器的设置。因此，一般来说，访问`www.example.com`这个网址，很可能返回的是网页文件`www.example.com/index.html`。

### 参数

参数（parameter）是提供给服务器的额外信息。参数的位置是在路径后面，它们之间使用`?`分隔，上例是`?key1=value1&key2=value2`。

每一组参数都是键值对（key-value pair）的形式，同时具有键名(key)和键值(value)，它们之间使用等号（`=`）连接。比如，`key1=value`就是一个键值对，`key1`是键名，`value1`是键值。

多组参数之间使用`&`连接，比如`key1=value1&key2=value2`。

参数通常不需要用户输入，网站会自动生成可点击的连接。参数具体名称和值，由各个网站自己设定。

### 锚点

锚点（anchor）是网页内部的定位点，`#`后名是锚点名称，放在网址的最后，比如`#anchor`。浏览器加载页面以后，会自动滚动到锚点所在的位置。

锚点名通过网页元素的`id`属性命名，详见《属性》一章。

## 合法字符和字符转义

URL 的各个组成部分，只能使用以下这些字符。

- 英语字母（包括大写和小写）
- 阿拉伯数字
- 连词号（`-`）
- 句号（`.`）
- 下划线（`_`）

此外，还有18个字符属于 URL 的保留字符，只能在给定的位置出现。如果用于其他目的，必须使用它们的转义形式。转义方法是在它们的十六进制 ASCII 码前面加上百分号（`%`）。下面是这18个字符及其转义形式。

- `!`：%21
- `#`：%23
- `$`：%24
- `&`：%26
- `'`：%27
- `(`：%28
- `)`：%29
- `*`：%2A
- `+`：%2B
- `,`：%2C
- `/`：%2F
- `:`：%3A
- `;`：%3B
- `=`：%3D
- `?`：%3F
- `@`：%40
- `[`：%5B
- `]`：%5D

举例来说，有一个网页的 URL 是`foo?bar.html`，那么需要写成`foo%3Fbar.html`。

URL 的合法字符，其实也可以采用这种转义方法，但是不建议使用。比如，字母`a`的十六进制 ASCII 码是`61`，转义形式后就是`%61`。因此，`www.apple.com`又可以写成`www.%61pple.com`，浏览器一样识别。

值得注意是，空格的转义形式是`%20`。对于那些包含空格的文件名，这个转义是必须的。

既不属于合法字符、也不属于保留字符的其他字符（比如汉字），理论上不需要转义，可以直接写在 URL 里面，比如`www.example.com/中国.html`。浏览器会自动将它们转义，发给服务器。转义方法是使用这些字符的十六进制 UTF-8 编码，每两位算作一组，然后每组头部添加百分号（`%`）。

举例来说，汉字`中`的 UTF-8 编码是`\xe4b8ad`，URL 转义后为`%e4%b8%ad`。也就是说，URL 里面凡是有汉字`中`的地方，都要写成`%e4%b8%ad`。因此，访问`www.example.com/中国.html`这个网址，需要写成下面的样子。

```html
www.example.com/%e4%b8%ad%e5%9b%bd.html
```

## 绝对 URL 和相对 URL

URL 分成两种：绝对 URL 和相对 URL。

绝对 URL 指的是，只靠 URL 本身就能确定资源的位置。这意味着，URL 必须带有资源的完整信息，包含协议、主机、路径等部分。

相对 URL 指的是，URL 不包含资源位置的全部信息，必须结合当前网页的位置，才能定位资源。比如，当前网页的 URL 是`https://www.example.com/path/index.html`，该网页上面有一个资源，URL 指向`a.html`，这个就是相对 URL。因为只知道`a.html`，并不能定位资源，还要知道当前网页的 URL 才可以。浏览器假定，`a.html`与当前网址在同一个子目录下面，从而经过转换，从相对 URL 得到绝对 URL `https://www.example.com/path/a.html`。

相对 URL 如果以斜杠（`/`）开头，就表示根目录。否则，必须以当前目录为起点，推算资源的位置。比如，相对 URL `foo/bar.html`表示在当前位置的`foo`子目录里面的`bar.html`文件。

相对 URL 还可以使用两个特殊写法，表示位置。

- `.`：表示当前目录，比如`./a.html`（当前目录下的`a.html`文件）
- `..`：表示上级目录，比如`../a.html`（上级目录下的`a.html`文件）

这两个写法可以多个连用，比如`../../`表示上两级目录。

## `<base>`

`<base>`标签指定网页内部所有相对 URL 的计算基准。整张网页只能有一个`<base>`标签，而且只能放在`<head>`里面。它是单独使用的标签，没有闭合标签，下面是一个例子。

```html
<head>
<base href="https://www.example.com/files/" target="_blank">
</head>
```

`<base>`标签的`href`属性给出计算的基准网址，`target`属性给出如何打开链接的说明（参见《链接》一章）。

已知计算基准是`https://www.example.com/files/`，那么相对 URL `foo.html`，就可以转成绝对 URL `https://www.example.com/files/foo.html`。

注意，`<base>`标签必须具有`href`属性或`target`属性。

