# meta

meta是网站源代码的html标签，用来描述html网页文档的属性，例如作者，日期和时间，网页描述，关键词，页面刷新等

meta 标签是一组键值对，它是一种通用的元信息表示标签。在 head 中可以出现任意多个 meta 标签。一般的 meta 标签由 name 和 content 两个属性来定义。name 表示元信息的名，content 则用于表示元信息的值。

## 常用的属性

```js
<meta charset="UTF-8">  // 声明当前文档所使用的字符编码,charset=”utf-8”是告知浏览器此页面属于什么字符编码格式，下一步浏览器做好“翻译”工作。常见的字符编码有：gb2312、gbk、unicode、utf-8。
  "UTF-8"or"utf-8" 该选择哪种写法？按照效果都是可以的，因为html属性是不区分大小写，，但是如果按照html的代码规范，建议使用小写
  （继续整理，参数）
<meta content=""> // 此属性始终要与name属性或者http-equiv属性一起使用
<meta name="keywords" content="biaoqian"> // 告诉搜索引擎呢网页的关键字
<meta name="description" content=""> // 网站描述的主要内容
<meta name="author" content="name"> // 描述网站的作者
<meta name ="robots" content ="all/none/index/noindex/follow/nofollow"> // 告诉搜索机器人页面需要或者不需要索引
  //all: 文件将被检索，且页面上的连接能够被查询
 // none: 文件不被检索，且页面上的连接不能够被查询
 // index: 文件将被检索
 // follow:页面上的连接能够被查询
  // noindex:文件将不被检索，但是页面上的连接能够被查询
  // nofollow:文件将不被检索，页面上的连接能够被查询
<meta name="viewport" content ="width=device-width,initial-scale=1.0">
  // width: 控制viewport的大小，可以指定一个值或者特殊值
  // height ：指定高度
  // initial-scale：初始缩放比例，这是一个浮点值，是页面大小的一个乘数。例如，如果你设置初始缩放为“1.0”，那么，web页面在展现的时候就会以target density分辨率的1:1来展现。如果你设置为“2.0”，那么这个页面就会放大为2倍。
  // maximun-scale ：允许用户缩放的最大比例
  // minimun-scale：允许用户缩放的最小比例
  // user-scalable： 用户是否可以手动缩放，如果设置为yes则是允许用户对其进行改变，反之为no。默认值是yes。如果你将其设置为no，那么minimum-scale 和 maximum-scale都将被忽略，因为根本不可能缩放。
  （继续整理，参数）
<meta name="renderder" content="webkit"> // 强制浏览器使用webkit内核
<meta http-equiv="refresh" content=""> // 定时让网页在指定时间内，跳转到你的页面（继续整理，参数）
<meta http-equiv="windows-target" content="_top"> // 强制页面在当前窗口中以独立页面显示，可以防止自己的网页被别人当作一个frame调用
<meta http-equiv="set-cookie" content="Mon,12 May 2001 00:20:00 GMT"> //cookie设定，如果网页过期，存盘的cookie将被删除。需要注意的也是必须使用GMT时间格式； 
 <meta http-equiv="Expires" content="Mon,12 May 2001 00:20:00 GMT">// 可以用于设定网页的到期时间，一旦过期则必须到服务器上重新调用。需要注意的是必须使用GMT时间格式；（继续整理，参数）
  <meta http-equiv="Page-Enter" content="revealTrans（duration=10,transition= 50）">和<meta http-equiv="Page-Exit" content="revealTrans（duration=20，transition=6）">设定进入和离开页面时的特殊效果，这个功能即FrontPage中的"格式/网页过渡"，不过所加的页面不能够是一个frame页面。（继续整理，参数）
  <meta http-equiv="Pics-label" content="">// 网页等级评定，在IE的internet选项中有一项内容设置，可以防止浏览一些受限制的网站，而网站的限制级别就是通过meta属性来设置的；（怎么设置在ie中具体的效果）
    <meta name="google" value="notranslate">//禁止 Chrome 浏览器中自动提示翻译
```



### 移动端

```js
<meta name="viewport" content="width=device-width, initial-scale=1.0,maximum-scale=1.0, user-scalable=no"/>
<!-- `width=device-width` 会导致 iPhone 5 添加到主屏后以 WebApp 全屏模式打开页面时出现黑边  -->
width：宽度（数值 / device-width）（范围从200 到10,000，默认为980 像素）
height：高度（数值 / device-height）（范围从223 到10,000）
initial-scale：初始的缩放比例 （范围从>0 到10）
minimum-scale：允许用户缩放到的最小比例
maximum-scale：允许用户缩放到的最大比例
user-scalable：用户是否可以手动缩 (no,yes)
minimal-ui：可以在页面加载时最小化上下状态栏。（已弃用）
注意，很多人使用initial-scale=1到非响应式网站上，这会让网站以100%宽度渲染，用户需要手动移动页面或者缩放。如果和initial-scale=1同时使用user-scalable=no或maximum-scale=1，则用户将不能放大/缩小网页来看到全部的内容。
WebApp全屏模式：伪装app，离线应用。
<meta name="apple-mobile-web-app-capable" content="yes" /> <!-- 启用 WebApp 全屏模式 -->
 隐藏状态栏/设置状态栏颜色：只有在开启WebApp全屏模式时才生效。content的值为default | black | black-translucent 。
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />
 添加到主屏后的标题
<meta name="apple-mobile-web-app-title" content="标题">
 忽略数字自动识别为电话号码
<meta content="telephone=no" name="format-detection" />
  忽略识别邮箱
<meta content="email=no" name="format-detection" />
  添加智能 App 广告条 Smart App Banner：告诉浏览器这个网站对应的app，并在页面上显示下载banner
<meta name="apple-itunes-app" content="app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL">
  <!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
<meta name="HandheldFriendly" content="true">
<!-- 微软的老式浏览器 -->
<meta name="MobileOptimized" content="320">
<!-- uc强制竖屏 -->
<meta name="screen-orientation" content="portrait">
<!-- QQ强制竖屏 -->
<meta name="x5-orientation" content="portrait">
<!-- UC强制全屏 -->
<meta name="full-screen" content="yes">
<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="true">
<!-- UC应用模式 -->
<meta name="browsermode" content="application">
<!-- QQ应用模式 -->
<meta name="x5-page-mode" content="app">
<!-- windows phone 点击无高光 -->
<meta name="msapplication-tap-highlight" content="no">
```

## pc

```js
申明编码
<meta charset='utf-8' />
优先使用 IE 最新版本和 Chrome
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
<!-- 关于X-UA-Compatible -->
<meta http-equiv="X-UA-Compatible" content="IE=6" ><!-- 使用IE6 -->
<meta http-equiv="X-UA-Compatible" content="IE=7" ><!-- 使用IE7 -->
<meta http-equiv="X-UA-Compatible" content="IE=8" ><!-- 使用IE8 -->
浏览器内核控制：国内浏览器很多都是双内核（webkit和Trident），webkit内核高速浏览，IE内核兼容网页和旧版网站。而添加meta标签的网站可以控制浏览器选择何种内核渲染。参考文档
<meta name="renderer" content="webkit|ie-comp|ie-stand">
国内双核浏览器默认内核模式如下：
1. 搜狗高速浏览器、QQ浏览器：IE内核（兼容模式）
2. 360极速浏览器、遨游浏览器：Webkit内核（极速模式）

禁止浏览器从本地计算机的缓存中访问页面内容：这样设定，访问者将无法脱机浏览。
<meta http-equiv="Pragma" content="no-cache">
Windows 8
<meta name="msapplication-TileColor" content="#000"/> <!-- Windows 8 磁贴颜色 -->
<meta name="msapplication-TileImage" content="icon.png"/> <!-- Windows 8 磁贴图标 -->
站点适配：主要用于PC-手机页的对应关系。
<meta name="mobile-agent"content="format=[wml|xhtml|html5]; url=url">
<!--
[wml|xhtml|html5]根据手机页的协议语言，选择其中一种；
url="url" 后者代表当前PC页所对应的手机页URL，两者必须是一一对应关系。
 -->
转码申明：用百度打开网页可能会对其进行转码（比如贴广告），避免转码可添加如下meta。
<meta http-equiv="Cache-Control" content="no-siteapp" />
  4.<meta name='spm-id' content='a21bo'>
说明:SPM是淘宝社区电商业务（xTao）为外部合作伙伴（外站）提供的一套跟踪引导成交效果数据的解决方案。
(1)SPM编码说明：用来跟踪页面模块位置的编码，标准spm编码由4段组成，采用a.b.c.d的格式（建议全部使用数字），其中，
(1-1)a代表站点类型，对于xTao合作伙伴（外站），a为固定值，a=2014
(1-2)b代表外站ID（即外站所使用的TOP appkey），比如您的站点使用的TOP appkey=123456789，则b=123456789
(1-3)c代表b站点上的频道ID，比如是外站某个团购频道，某个逛街频道，某个试用频道 等
(1-4)d代表c频道上的页面ID，比如是某个团购详情页，某个宝贝详情页，某个试用详情页 等

```

 除了基本用法，meta 标签还有一些变体，主要用于简化书写方式或者声明自动化行为.

具有 charset 属性的 meta

从 HTML5 开始，为了简化写法，meta 标签新增了 charset 属性。添加了 charset 属性的 meta 标签无需再有 name 和 content。 charset 型 meta 标签非常关键，它描述了 HTML 文档自身的编码形式。因此，我建议这个标签放在 head 的第一个。……这样，浏览器读到这个标签之前，处理的所有字符都是 ASCII 字符，众所周知，ASCII 字符是 UTF-8 和绝大多数字符编码的子集，所以，在读到 meta 之前，浏览器把文档理解多数编码格式都不会出错，这样可以最大限度地保证不出现乱码。一般情况下，HTTP 服务端会通过 http 头来指定正确的编码方式，但是有些特殊的情况如使用 file 协议打开一个 HTML 文件，则没有 http 头，这种时候，charset meta 就非常重要了。

具有 http-equiv 属性的 meta

具有 http-equiv 属性的 meta 标签，表示执行一个命令，这样的 meta 标签可以不需要 name 属性了

<meta http-equiv="content-type" content="text/html; charset=UTF-8">

除了 content-type，还有以下几种命令：content-language 指定内容的语言；default-style 指定默认样式表；refresh 刷新；set-cookie 模拟 http 头 set-cookie，设置 cookie；x-ua-compatible 模拟 http 头 x-ua-compatible，声明 ua 兼容性；content-security-policy 模拟 http 头 content-security-policy，声明内容安全策略。

name 为 viewport 的 meta

实际上，meta 标签可以被自由定义，只要写入和读取的双方约定好 name 和 content 的格式就可以了。我们来介绍一个 meta 类型，它没有在 HTML 标准中定义，却是移动端开发的事实标准：它就是 name 为 viewport 的 meta。这类 meta 的 name 属性为 viewport，它的 content 是一个复杂结构，是用逗号分隔的键值对，键值对的格式是 key=value。

<meta name="viewport" content="width=500, initial-scale=1">

这里只指定了两个属性，宽度和缩放，实际上 viewport 能控制的更多，它能表示的全部属性如下：width：页面宽度，可以取值具体的数字，也可以是 device-width，表示跟设备宽度相等。height：页面高度，可以取值具体的数字，也可以是 device-height，表示跟设备高度相等。initial-scale：初始缩放比例。minimum-scale：最小缩放比例。maximum-scale：最大缩放比例。user-scalable：是否允许用户缩放。

对于已经做好了移动端适配的网页，应该把用户缩放功能禁止掉，宽度设为设备宽度，一个标准的 meta 如下：

<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no">

其它预定义的 meta

在 HTML 标准中，还定义了一批 meta 标签的 name，可以视为一种有约定的 meta，我在这里列出来，你可以简单了解一下。application-name：如果页面是 Web application，用这个标签表示应用名称。author: 页面作者。description：页面描述，这个属性可能被用于搜索引擎或者其它场合。generator: 生成页面所使用的工具，主要用于可视化编辑器，如果是手写 HTML 的网页，不需要加这个 meta。keywords: 页面关键字，对于 SEO 场景非常关键。referrer: 跳转策略，是一种安全考量。theme-color: 页面风格颜色，实际并不会影响页面，但是浏览器可能据此调整页面之外的 UI（如窗口边框或者 tab 的颜色）。

##  link 标签

link 标签也是元信息的一种，在很多时候，它也是不会对浏览器产生任何效果的，这也是很多人会忽略 link 标签学习的原因。

ink 标签会生成一个链接，它可能生成超链接，也可能生成外部资源链接。一些 link 标签会生成超链接，这些超链接又不会像 a 标签那样显示在网页中。这就是超链接型的 link 标签。这意味着多数浏览器中，这些 link 标签不产生任何作用。但是，这些 link 标签能够被搜索引擎和一些浏览器插件识别，从而产生关键性作用。

另外一些 link 标签则会把外部的资源链接到文档中，也就是说，会实际下载这些资源，并且做出一些处理，比如我们常见的用 link 标签引入样式表。除了元信息的用法之外，多数外部资源型的 link 标签还能够被放在 body 中使用，从而起到把外部资源链接进文档的作用。

link 标签的链接类型主要通过 rel 属性来区分，在本篇文章中，我们提到 xx 型 link 即表示属性 rel 为 xx 的 link，其代码类似下面：

<link rel="xx" ...>

### 超链接类 link 标签

超链接型 link 标签是一种被动型链接，在用户不操作的情况下，它们不会被主动下载。link 标签具有特定的 rel 属性，会成为特定类型的 link 标签。产生超链接的 link 标签包括：具有 rel=“canonical” 的 link、具有 rel="alternate"的 link、具有 rel=“prev” rel="next"的 link 等等。

#### canonical 型 link

<link rel="canonical" href="...">

这个标签提示页面它的主 URL，在网站中常常有多个 URL 指向同一页面的情况，搜索引擎访问这类页面时会去掉重复的页面，这个 link 会提示搜索引擎保留哪一个 URL。

#### alternate 型 link

<link rel="alternate" href="...">

这个标签提示页面它的变形形式，这个所谓的变形可能是当前页面内容的不同格式、不同语言或者为不同的设备设计的版本，这种 link 通常也是提供给搜索引擎来使用的。alternate 型的 link 的一个典型应用场景是，页面提供 rss 订阅时，可以用这样的 link 来引入：

<link rel="alternate" type="application/rss+xml" title="RSS" href="...">

除了搜索引擎外，很多浏览器插件都能识别这样的 link。

#### prev 型 link 和 next 型 link

在互联网应用中，很多网页都属于一个序列，比如分页浏览的场景，或者图片展示的场景，每个网页是序列中的一个项。这种时候，就适合使用 prev 和 next 型的 link 标签，来告诉搜索引擎或者浏览器它的前一项和后一项，这有助于页面的批量展示。因为 next 型 link 告诉浏览器“这是很可能访问的下一个页面”，HTML 标准还建议对 next 型 link 做预处理，在本课后面的内容，我们会讲到预处理类的 link。

#### 其它超链接类的 link

其它超链接类 link 标签都表示一个跟当前文档相关联的信息，可以把这样的 link 标签视为一种带链接功能的 meta 标签。rel=“author” 链接到本页面的作者，一般是 mailto: 协议rel=“help” 链接到本页面的帮助页rel=“license” 链接到本页面的版权信息页rel=“search” 链接到本页面的搜索页面（一般是站内提供搜索时使用）

### 外部资源类 link 标签

外部资源型 link 标签会被主动下载，并且根据 rel 类型做不同的处理。外部资源型的标签包括：具有 icon 型的 link、预处理类 link、modulepreload 型的 link、stylesheet、pingback。下面我们来一一介绍它们。

#### icon 型 link

这类链接表示页面的 icon。多数浏览器会读取 icon 型 link，并且把页面的 icon 展示出来。icon 型 link 是唯一一个外部资源类的元信息 link，其它元信息类 link 都是超链接，这意味着，icon 型 link 中的图标地址默认会被浏览器下载和使用。如果没有指定这样的 link，多数浏览器会使用域名根目录下的 favicon.ico，即使它并不存在，所以从性能的角度考虑，建议一定要保证页面中有 icon 型的 link。只有 icon 型 link 有有效的 sizes 属性，HTML 标准允许一个页面出现多个 icon 型 link，并且用 sizes 指定它适合的 icon 尺寸

#### 预处理类 link

我们都知道，导航到一个网站需要经过 dns 查询域名、建立连接、传输数据、加载进内存和渲染等一系列的步骤。预处理类 link 标签就是允许我们控制浏览器，提前针对一些资源去做这些操作，以提高性能（当然如果你乱用的话，性能反而更差）。

下面我来列一下这些 link 类型：

dns-prefetch 型 link 提前对一个域名做 dns 查询，这样的 link 里面的 href 实际上只有域名有意义。

preconnect 型 link 提前对一个服务器建立 tcp 连接。

prefetch 型 link 提前取 href 指定的 url 的内容。

preload 型 link 提前加载 href 指定的 url。prerender 型 link 提前渲染 href 指定的 url。

#### modulepreload 型的 link

modulepreload 型 link 的作用是预先加载一个 JavaScript 的模块。这可以保证 JS 模块不必等到执行时才加载。这里的所谓加载，是指完成下载并放入内存，并不会执行对应的 JavaScript

<link rel="modulepreload" href="app.js">
<link rel="modulepreload" href="helpers.js">
<link rel="modulepreload" href="irc.js">
<link rel="modulepreload" href="fog-machine.js">

<script type="module" src="app.js"> 

这个例子来自 HTML 标准，我们假设 app.js 中有 import “irc” 和 import “fog-machine”, 而 irc.js 中有 import “helpers”。这段代码使用 moduleload 型 link 来预加载了四个 js 模块。

尽管，单独使用 script 标签引用 app.js 也可以正常工作，但是我们通过加入对四个 JS 文件的 link 标签，使得四个 JS 文件有机会被并行地下载，这样提高了性能。

#### stylesheet 型 link

<link rel="stylesheet" href="xxx.css" type="text/css">

基本用法是从一个 CSS 文件创建一个样式表。这里 type 属性可以没有，如果有，必须是"text/css"才会生效。

rel 前可以加上 alternate，成为 rel=“alternate stylesheet”，此时必须再指定 title 属性。

这样可以为页面创建一份变体样式，一些浏览器，如 Firefox 3.0，支持从浏览器菜单中切换这些样式，当然了，大部分浏览器不支持这个功能，所以仅仅从语义的角度了解一下这种用法即可。

#### pingback 型 link

这样的 link 表示本网页被引用时，应该使用的 pingback 地址，这个机制是一份独立的标准，遵守 pingback 协议的网站在引用本页面时，会向这个 pingback url 发送一个消息。

## a标签

a 标签其实同时充当了链接和目标点的角色，当 a 标签有 href 属性时，它是链接，当它有 name 时，它是链接的目标。具有 href 的 a 标签跟一些 link 一样，会产生超链接，也就是在用户不操作的情况下，它们不会被主动下载的被动型链接。

重点的内容是，a 标签也可以有 rel 属性，我们来简单了解一下，首先是跟 link 相同的一些 rel，包括下面的几种。alternate author help license next prev search

这些跟 link 语义完全一致，不同的是，a 标签产生的链接是会实际显示在网页中的，而 link 标签仅仅是元信息。除了这些之外，a 标签独有的 rel 类型：

tag 表示本网页所属的标签；

bookmark 到上级章节的链接。

a 标签还有一些辅助的 rel 类型，用于提示浏览器或者搜索引擎做一些处理：

nofollow 此链接不会被搜索引擎索引；

noopener 此链接打开的网页无法使用 

opener 来获得当前页面的窗口；

noreferrer 此链接打开的网页无法使用 

referrer 来获得当前页面的 url；

opener 打开的网页可以使用 window.opener 来访问当前页面的 window 对象，这是 a 标签的默认行为。

a 标签基本解决了在页面中插入文字型和整张图片超链接的需要，但是如果我们想要在图片的某个区域产生超链接，那么就要用到另一种标签了——area 标签。

## area

area 标签与 a 标签非常相似，不同的是，它不是文本型的链接，而是区域型的链接。area 标签支持的 rel 与 a 完全一样，

area 是整个 html 规则中唯一支持非矩形热区的标签，它的 shape 属性支持三种类型。圆形：circle 或者 circ，coords 支持三个值，分别表示中心点的 x,y 坐标和圆形半径 r。矩形：rect 或者 rectangle，coords 支持两个值，分别表示两个对角顶点 x1，y1 和 x2，y2。多边形：poly 或者 polygon，coords 至少包括 6 个值，表示多边形的各个顶点。因为 area 设计的时间较早，所以不支持含有各种曲线的路径，但是它也是唯一一个支持了非矩形触发区域的元素，所以，对于一些效果而言，area 是必不可少的。

area 必须跟 img 和 map 标签配合使用。使用示例如下

<p>
 Please select a shape:
 <img src="shapes.png" usemap="#shapes"
      alt="Four shapes are available: a red hollow box, a green circle, a blue triangle, and a yellow four-pointed star.">
 <map name="shapes">
  <area shape=rect coords="50,50,100,100"> <!-- the hole in the red box -->
  <area shape=rect coords="25,25,125,125" href="red.html" alt="Red box.">
  <area shape=circle coords="200,75,50" href="green.html" alt="Green circle.">
  <area shape=poly coords="325,25,262,125,388,125" href="blue.html" alt="Blue triangle.">
  <area shape=poly coords="450,25,435,60,400,75,435,90,450,125,465,90,500,75,465,60"
        href="yellow.html" alt="Yellow star.">
 </map>
</p>

//这个例子展示了在一张图片上画热区并且产生链接，分别使用了矩形、圆形和多边形三种 area。

link 标签一般用于看不见的链接，它可能产生超链接或者外部资源链接，a 和 area 一般用于页面上显示的链接，它们只能产生超链接。