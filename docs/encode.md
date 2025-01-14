# HTML 字符编码

## 简介

网页包含了大量的文字，浏览器必须知道这些文字的编码方法，才能把文字还原出来。

一般情况下，服务器向浏览器发送 HTML 网页文件时，会通过 HTTP 头信息，声明网页的编码方式。

```http
Content-Type: text/html; charset=UTF-8
```

网页内部也会再用`<meta>`标签，再次声明网页的编码。

```html
<meta charset="UTF-8">
```

## 字符的数字表示法

网页可以使用不同语言的编码方式，但是最常用的编码是 UTF-8。UTF-8 编码是 Unicode 字符集的一种表达方式。这个字符集的设计目标是包含世界上的所有字符，目前已经收入了十多万个字符。

每个字符有一个 Unicode 号码，称为码点（code point）。如果知道码点，就能查到这是什么字符。举例来说，英文字母`a`的码点是十进制的`97`（十六进制的`61`），汉字“中”的码点是十进制的`20013`（十六进制的`4e2d`）。

HTML 为了解决下面这些问题，允许网页字符以码点表示，浏览器会自动将码点转成对应的字符。

> - 有些 Unicode 字符是不可打印的，没有字面形式，比如换行符。
> - 小于号（`<`）和大于号（`>`）用来定义标签，有些场合要用到这两个符号，必须防止它们被解释成标签。
> - 由于 Unicode 字符太多，无法找到一种输入法，可以直接输入所有这些字符。
> - 网页不允许混合使用多种编码，如果不使用 UTF-8 编码，同时又想插入其他编码的字符，就会很困难。

HTML 里面的码点表示方法是`&#N;`（十进制）或者`&#xN;`（十六进制），其中的`N`就是字符的码点。比如，字符`a`可以写成`&#97;`（十进制）或者`&#x61;`（十六进制），字符`中`写成`&#20013;`（十进制）或者`&#x4e2d;`（十六进制），浏览器会自动转换它们。

## 字符的实体表示法

数字表示法的不方便之处，在于必须知道每个字符的码点。为了能够快速输入，HTML 为大量的特殊字符，规定了容易记忆的名字，允许通过名字来表示它们，这称为实体表示法（entity）。

实体的写法是`&name;`，其中的`name`是字符的名称。下面是其中一些特殊字符，及其对应的实体。

- `<`：`&lt;`
- `>`：`&gt;`
- `"`：`&quot;`
- `'`：`&apos;`
- `&`：`&amp;`
- `©`：`&copy;`
- `#`：`&num;`
- `§`：`&sect;`
- `¥`：`&yen;`
- `$`：`&dollar;`
- `£`：`&pound;`
- `¢`：`&cent;`
- `%`：`&percnt;`
- `*`：`$ast;`
- `@`：`&commat;`
- `^`：`&Hat;`
- `±`：`&plusmn;`
- 空格：`&nbsp;`

注意，上面最后一个特殊字符是空格，它也有对应的实体表示法。

字符的数字表示法和实体表示法，都可以表示正常情况无法输入的字符，逃脱了浏览器的限制，所以英语里面称为“escape”，中文翻译为“字符的转移”。
