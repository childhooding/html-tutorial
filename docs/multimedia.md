# 多媒体

除了图像，网页还可以放置视频和音频。

## `<video>`

`<video>`标签是一个块级元素，用于放置视频，浏览器支持该种视频格式，就是显示一个播放器，否则显示`<video>`内部的子元素。

```html
<video src="example.mp4" controls>
  <p>你的浏览器不支持 HTML5 视频，请下载<a href="example.mp4">视频文件</a>。</p>
</video>
```

上面代码中，如果浏览器不支持该种格式的视频，就会显示提示。

`<video>`有以下属性。

- `src`：视频文件的网址。
- `controls`：播放器是否显示控制栏。该属性是布尔属性，不用赋值，只要写上属性名，就表示打开。
- `width`：视频播放器的宽度，单位像素。
- `height`：视频播放器的高度，单位像素。
- `autoplay`：视频是否自动播放，该属性为布尔属性。
- `loop`：视频是否循环播放，该属性为布尔属性。
- `muted`：是否默认静音，该属性为布尔属性。
- `poster`：视频播放器的封面图片的 URL。
- `preload`：视频播放之前，是否缓冲视频文件。这个属性仅适合没有设置`autoplay`的情况。它有三个值，分别是`none`（不缓冲）、`metadata`（仅仅缓冲视频文件的元数据）、`auto`（可以缓冲整个文件）。
- `playsinline`：iPhone 的 Safari 浏览器播放视频时，会自动全屏，该属性可以禁止这种行为。该属性为布尔属性。
- `crossorigin`：是否采用跨域的方式加载视频。它可以取两个值，分别是`anonymous`（跨域请求时，不发送用户凭证，主要是 Cookie），`use-credentials`（跨域时发送用户凭证）。

下面是一个例子。

```html
<video controls width="400" height="400"
       autoplay loop muted
       poster="poster.png">
</video>
```

上面代码中，视频播放器的大小是 400 x 400，会自动播放和循环播放，并且静音，还带有封面图。这是网站首页背景视频的常见写法。

HTML 标准没有规定浏览器需要支持哪些视频格式，完全由浏览器厂商自己决定。为了避免浏览器不支持视频格式，可以使用`<source>`标签，放置同一个视频的多种格式。

```html
<video controls>
  <source src="example.mp4" type="video/mp4">
  <source src="example.webm" type="video/webm">
  <p>你的浏览器不支持 HTML5 视频，请下载<a href="example.mp4">视频文件</a>。</p>
</video>
```

上面代码中，`<source>`标签的`type`属性的值是视频文件的 MIME 类型，上例指定了两种格式的视频文件：MP4 和 WebM。如果浏览器支持 MP4，就加载 MP4 格式的视频，不再往下执行了。如果不支持 MP4，就检查是否支持 WebM，如果还是不支持，则显示提示。
