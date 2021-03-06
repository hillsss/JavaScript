# HTML

**1.**  *DOCTYPE(⽂档类型) 的作⽤*
+ DOCTYPE是HTML5中一种标准通用标记语言的文档类型声明，它的目的是**告诉浏览器（解析器）应该以什么样（html或xhtml）的文档类型定义来解析文档**，不同的渲染模式会影响浏览器对 CSS 代码甚⾄ JavaScript 脚本的解析。它必须声明在HTML⽂档的第⼀⾏。

**2.** *src和href的区别*
src和href都是用来**引用外部的资源**，它们的区别如下：

+ **src**： 表示对**资源的引用**，它指向的内容会嵌入到当前标签所在的位置。src会将其指向的资源下载并应⽤到⽂档内，如请求js脚本。当浏览器解析到该元素时，会暂停其他资源的下载和处理，直到将该资源加载、编译、执⾏完毕，所以⼀般js脚本会放在页面底部。
+ **href**： 表示**超文本引用**，它指向一些网络资源，建立和当前元素或本文档的链接关系。当浏览器识别到它他指向的⽂件时，就会并⾏下载资源，不会停⽌对当前⽂档的处理。 常用在a、link等标签上。

**3.** *script标签中defer和async的区别*
如果没有defer或async属性，浏览器会立即加载并执行相应的脚本。它不会等待后续加载的文档元素，读取到就会开始加载和执行，这样就阻塞了后续文档的加载。
下图可以直观的看出三者之间的区别:

![script-async-defer.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b0a8a139519f46dfa2d1992c58eb5397~tplv-k3u1fbpfcp-zoom-in-crop-mark:1304:0:0:0.awebp)


其中蓝色代表js脚本网络加载时间，红色代表js脚本执行时间，绿色代表html解析。
**defer 和 async属性都是去异步加载外部的JS脚本文件**，它们都不会阻塞页面的解析，其区别如下：

执行顺序： 多个带async属性的标签，不能保证加载的顺序；多个带defer属性的标签，按照加载顺序执行；
脚本是否并行执行：async属性，表示后续文档的加载和执行与js脚本的加载和执行是并行进行的，即异步执行；defer属性，加载后续文档的过程和js脚本的加载(此时仅加载不执行)是并行进行的(异步)，js脚本需要等到文档所有元素解析完成之后才执行，DOMContentLoaded事件触发执行之前。


**4.** *对HTML语义化的理解*
**语义化是指根据内容的结构化（内容语义化），选择合适的标签（代码语义化）**。通俗来讲就是用正确的标签做正确的事情。
语义化的优点如下：
+ 对机器友好，带有语义的文字表现力丰富，更适合搜索引擎的爬虫爬取有效信息，有利于SEO。除此之外，语义类还支持读屏软件，根据文章可以自动生成目录；
+ 对开发者友好，使用语义类标签增强了可读性，结构更加清晰，开发者能清晰的看出网页的结构，便于团队的开发与维护。
``` 
<header></header>  头部

<nav></nav>  导航栏

<section></section>  区块（有语义化的div）

<main></main>  主要区域

<article></article>  主要内容

<aside></aside>  侧边栏

<footer></footer>  底部
```

**5.** *常⽤的meta标签有哪些*
meta 标签由 name 和 content 属性定义，**用来描述网页文档的属性**，比如网页的作者，网页描述，关键词等，除了HTTP标准固定了一些name作为大家使用的共识，开发者还可以自定义name。
常用的meta标签：
（1）charset，用来描述HTML文档的编码类型：
```
<meta charset="UTF-8" >
```

（2） keywords，页面关键词：
```
<meta name="keywords" content="关键词" />
```

（3）description，页面描述：
```
<meta name="description" content="页面描述内容" />
```

（4）refresh，页面重定向和刷新：
```
<meta http-equiv="refresh" content="0;url=" />
```
（5）viewport，适配移动端，可以控制视口的大小和比例：
```
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
```
其中，content 参数有以下几种：

width viewport ：宽度(数值/device-width)
height viewport ：高度(数值/device-height)
initial-scale ：初始缩放比例
maximum-scale ：最大缩放比例
minimum-scale ：最小缩放比例
user-scalable ：是否允许用户缩放(yes/no）

（6）搜索引擎索引方式：
```
<meta name="robots" content="index,follow" />
```
其中，content 参数有以下几种：

all：文件将被检索，且页面上的链接可以被查询；
none：文件将不被检索，且页面上的链接不可以被查询；
index：文件将被检索；
follow：页面上的链接可以被查询；
noindex：文件将不被检索；
nofollow：页面上的链接不可以被查询。

**6.** *HTML5有哪些更新*
1. 语义化标签

+ header：定义文档的页眉（头部）；
+ nav：定义导航链接的部分；
+ footer：定义文档或节的页脚（底部）；
+ article：定义文章内容；
+ section：定义文档中的节（section、区段）；
+ aside：定义其所处内容之外的内容（侧边）；
2. 媒体标签

（1） audio：音频
```
<audio src='' controls autoplay loop='true'></audio>
```
属性：

+ controls 控制面板
+ autoplay 自动播放
+ loop=‘true’ 循环播放

（2）video视频
```
<video src='' poster='imgs/aa.jpg' controls></video>
```
属性：

+ poster：指定视频还没有完全下载完毕，或者用户还没有点击播放前显示的封面。默认显示当前视频文件的第一针画面，当然通过poster也可以自己指定。
+ controls 控制面板
+ width
+ height

（3）source标签 因为浏览器对视频格式支持程度不一样，为了能够兼容不同的浏览器，可以通过source来指定视频源。
```
<video>
 	<source src='aa.flv' type='video/flv'></source>
 	<source src='aa.mp4' type='video/mp4'></source>
</video>
```

3. 表单

表单类型：

+ email ：能够验证当前输入的邮箱地址是否合法
+ url ： 验证URL
+ number ： 只能输入数字，其他输入不了，而且自带上下增大减小箭头，max属性可以设置为最大值，min可以设置为最小值，value为默认值。
+ search ： 输入框后面会给提供一个小叉，可以删除输入的内容，更加人性化。
+ range ： 可以提供给一个范围，其中可以设置max和min以及value，其中value属性可以设置为默认值
+ color ： 提供了一个颜色拾取器
+ time ： 时分秒
+ data ： 日期选择年月日
+ datatime ： 时间和日期(目前只有Safari支持)
+ datatime-local ：日期时间控件
+ week ：周控件
+ month：月控件

表单属性：

+ placeholder ：提示信息
+ autofocus ：自动获取焦点
+ autocomplete=“on” 或者 autocomplete=“off” 使用这个属性需要有两个前提：
    - 表单必须提交过
    - 必须有name属性。
+ required：要求输入框不能为空，必须有值才能够提交。
+ pattern=" " 里面写入想要的正则模式，例如手机号patte="^(+86)?\d{10}$"
+ multiple：可以选择多个文件或者多个邮箱
+ form=" form表单的ID"

表单事件：

+ oninput 每当input里的输入框内容发生变化都会触发此事件。
+ oninvalid 当验证不通过时触发此事件。

4. 进度条、度量器

+ progress标签：用来表示任务的进度（IE、Safari不支持），max用来表示任务的进度，value表示已完成多少
+ meter属性：用来显示剩余容量或剩余库存（IE、Safari不支持）

    + high/low：规定被视作高/低的范围
    + max/min：规定最大/小值
    + value：规定当前度量值

设置规则：min < low < high < max

5. DOM查询操作

+ document.querySelector()
+ document.querySelectorAll()

它们选择的对象可以是标签，可以是类(需要加点)，可以是ID(需要加#)

6. Web存储

HTML5 提供了两种在客户端存储数据的新方法：
+ localStorage - 没有时间限制的数据存储
+ sessionStorage - 针对一个 session 的数据存储

7. 其他

+ 拖放：拖放是一种常见的特性，即抓取对象以后拖到另一个位置。设置元素可拖放：
```
<img draggable="true" />
```
+ 画布（canvas ）： canvas 元素使用 JavaScript 在网页上绘制图像。画布是一个矩形区域，可以控制其每一像素。canvas 拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。
```
<canvas id="myCanvas" width="200" height="100"></canvas>
```
+ SVG：SVG 指可伸缩矢量图形，用于定义用于网络的基于矢量的图形，使用 XML 格式定义图形，图像在放大或改变尺寸的情况下其图形质量不会有损失，它是万维网联盟的标准
+ 地理定位：Geolocation（地理定位）用于定位用户的位置。

**总结**：
（1）新增语义化标签：nav、header、footer、aside、section、article
（2）音频、视频标签：audio、video
（3）数据存储：localStorage、sessionStorage
（4）canvas（画布）、Geolocation（地理定位）、websocket（通信协议）
（5）input标签新增属性：placeholder、autocomplete、autofocus、required
（6）history API：go、forward、back、pushstate

**移除的元素有**：
+ 纯表现的元素：basefont，big，center，font, s，strike，tt，u;
+ 对可用性产生负面影响的元素：frame，frameset，noframes；

**7.** *行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？*
+ 行内元素有：a  span img input select strong；
+ 块级元素有：div ul ol li dl dt dd h1-h6 p；

空元素，即没有内容的HTML元素。空元素是在开始标签中关闭的，也就是空元素没有闭合标签：

+ 常见的有：`<br>、<hr>、<img>、<input>、<link>、<meta>；`
+ 鲜见的有：`<area>、<base>、<col>、<colgroup>、<command>、<embed>、<keygen>、<param>、<source>、<track>、<wbr>。`

**8.** *说一下 web worker*

在 HTML 页面中，如果在执行脚本时，页面的状态是不可响应的，直到脚本执行完成后，页面才变成可响应。web worker 是运行在后台的 js，独立于其他脚本，不会影响页面的性能。 并且通过 postMessage 将结果回传到主线程。这样在进行复杂操作的时候，就不会阻塞主线程了。

如何创建 web worker：

1. 检测浏览器对于 web worker 的支持性
2. 创建 web worker 文件（js，回传函数等）
3. 创建 web worker 对象

**9.** *title与h1的区别、b与strong的区别、i与em的区别？*

+ strong标签有语义，是起到加重语气的效果，而b标签是没有的，b标签只是一个简单加粗标签。b标签之间的字符都设为粗体，strong标签加强字符的语气都是通过粗体来实现的，而搜索引擎更侧重strong标签。
+ title属性没有明确意义只表示是个标题，H1则表示层次明确的标题，对页面信息的抓取有很大的影响
+ i内容展示为斜体，em表示强调的文本

**10.** *iframe 有那些优点和缺点？*

iframe 元素会创建包含另外一个文档的内联框架（即行内框架）。
**优点**：

+ 用来加载速度较慢的内容（如广告）
+ 可以使脚本可以并行下载
+ 可以实现跨子域通信

**缺点**：

+ iframe 会阻塞主页面的 onload 事件
+ 无法被一些搜索引擎索识别
+ 会产生很多页面，不容易管理

**11.** *label 的作用是什么？如何使用？*
label标签来定义表单控件的关系：当用户选择label标签时，浏览器会自动将焦点转到和label标签相关的表单控件上。

+ 使用方法1：
```
<label for="mobile">Number:</label>
<input type="text" id="mobile"/>
```
+ 使用方法2：
```
<label>Date:<input type="text"/></label>
```
**12.** *Canvas和SVG的区别*
（1）SVG：
SVG可缩放矢量图形（Scalable Vector Graphics）是基于可扩展标记语言XML描述的2D图形的语言，SVG基于XML就意味着SVG DOM中的每个元素都是可用的，可以为某个元素附加Javascript事件处理器。在 SVG 中，每个被绘制的图形均被视为对象。如果 SVG 对象的属性发生变化，那么浏览器能够自动重现图形。
其特点如下：
+ 不依赖分辨率
+ 支持事件处理器
+ 最适合带有大型渲染区域的应用程序（比如谷歌地图）
+ 复杂度高会减慢渲染速度（任何过度使用 DOM 的应用都不快）
+ 不适合游戏应用

（2）Canvas：
Canvas是画布，通过Javascript来绘制2D图形，是逐像素进行渲染的。其位置发生改变，就会重新进行绘制。
其特点如下：

+ 依赖分辨率
+ 不支持事件处理器
+ 弱的文本渲染能力
+ 能够以 .png 或 .jpg 格式保存结果图像
+ 最适合图像密集型的游戏，其中的许多对象会被频繁重绘

注：矢量图，也称为面向对象的图像或绘图图像，在数学上定义为一系列由线连接的点。矢量文件中的图形元素称为对象。每个对象都是一个自成一体的实体，它具有颜色、形状、轮廓、大小和屏幕位置等属性。
