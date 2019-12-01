# css排版

正常流的排版行为，那就是：依次排列，排不下了换行

## 等分布局问题

横向等分布局是一个很常见的需求，按照一般的思路，我们可以使用百分比宽度来解决，我们参考以下代码：


<div class="outer">
    <div class="inner"></div>
    <div class="inner"></div>
    <div class="inner"></div>
</div>
.inner {
    width:33.33%;
    height:300px;
    display:inline-block;
    outline:solid 1px blue;
}

在这段 HTML 代码中，我们放了三个 div，用 CSS 给它们指定了百分比宽度，并且指定为 inline-block。但是这段代码执行之后，效果跟我们预期不同，我们可以发现，每个 div 并非紧挨，中间有空白，这是因为我们为了代码格式加入的换行和空格被 HTML 当作空格文本，跟 inline 盒混排了的缘故。

解决方案是修改 HTML 代码，去掉空格和换行：

<div class="outer"><div class="inner"></div><div class="inner"></div><div class="inner"></div></div>

但是这样做影响了源代码的可读性，一个变通的方案是，改变 outer 中的字号为 0。

.inner {
    width:33.33%;
    height:300px;
    display:inline-block;
    outline:solid 1px blue;
    font-size:30px;
}
.outer {
    font-size:0;
}

在某些浏览器中，因为像素计算精度问题，还是会出现换行，我们给 outer 添加一个特定宽度

.inner {
    width:33.33%;
    height:300px;
    display:inline-block;
    outline:solid 1px blue;
}
.outer {
    width:101px
}

这个代码在某些旧版本浏览器中会出现换行。为了保险起见，我们给最后一个 div 加上一个负的右 margin：

.outer {
    width:101px
}

.inner {
    width:33.33%;
    height:300px;
    display:inline-block;
    outline:solid 1px blue;
}

.inner:last-child {
    margin-right:-5px;
}

这样就可以解决旧版本浏览器的问题了。除了使用 inline-block，float 也可以实现类似的效果，但是 float 元素只能做顶对齐，不如 inline-block 灵活。

## 自适应宽

我们再来说说自适应宽。在 IE6 统治浏览器市场的旧时代，自适应宽（一个元素固定宽度，另一个元素填满父容器剩余宽度）是个经典的布局问题，我们现在就看一下如何使用正常流来解决。

<div class="outer">
    <div class="fixed"></div>
    <div class="auto"></div>
</div>
.fixed {
    width:200px;
}
.fixed, .auto {
    height:300px;
    outline:solid 1px blue;
}

使用正常流解决这个问题的思路是，利用负 margin：

.fixed {
    display:inline-block;
    vertical-align:top;
}
.auto {
    margin-left:-200px;
    width:100%;
    display:inline-block;
    vertical-align:top;
}

但是，这样做会导致 auto 中的内容位置不对，所以我们还需要使用 padding 把内容挤出来，最终完整代码如下

.fixed {
    display:inline-block;
    vertical-align:top;
}
.auto {
    margin-left:-200px;
    padding-left:200px;
    box-sizing:border-box;
    width:100%;
    display:inline-block;
    vertical-align:top;
}

这样就给 auto 添加了 padding-left 和 box-sizing 两个属性。

总的来说，正常流布局主要是使用 inline-block 来作为内容的容器，利用块级格式化上下文的纵向排布和行内级格式化上下文的横向排布来完成布局的，我们需要根据需求的横向和纵向排布要求，来选择元素的 display 属性。

# html替换元素：为什么link一个css要用href,而引入js要用src

## script

script 标签是为数不多的既可以作为替换型标签，又可以不作为替换型标签的元素。

## img

最熟悉的替换型标签就是 img 标签了

img 标签的作用是引入一张图片。这个标签是没有办法像 script 标签那样作为非替换型标签来使用的，它必须有 src 属性才有意义。

 此处要重点提到一个属性，alt 属性，这个属性很难被普通用户感知，对于视障用户非常重要，可以毫不夸张地讲，给 img 加上 alt 属性，已经做完了可访问性的一半。

img 标签还有一组重要的属性，那就是 srcset 和 sizes，它们是 src 属性的升级版（所以我们前面讲 img 标签必须有 src 属性，这是不严谨的说法）。

这两个属性的作用是在不同的屏幕大小和特性下，使用不同的图片源。下面一个例子也来自 MDN，它展示了 srcset 和 sizes 的用法

<img srcset="elva-fairy-320w.jpg 320w,
             elva-fairy-480w.jpg 480w,
             elva-fairy-800w.jpg 800w"
     sizes="(max-width: 320px) 280px,
            (max-width: 480px) 440px,
            800px"
     src="elva-fairy-800w.jpg" alt="Elva dressed as a fairy">

srcset 提供了根据屏幕条件选取图片的能力，但是其实更好的做法，是使用 picture 元素

## picture

<picture>
  <source srcset="image-wide.png" media="(min-width: 600px)">
  <img src="image-narrow.png">
</picture>

picture 元素的设计跟 audio 和 video 保持了一致（稍后我会为你讲解这两个元素），它跟 img 搭配 srcset 和 sizes 不同，它使用 source 元素来指定图片源，并且支持多个。这里的 media 属性是 media query，跟 CSS 的 @media 规则一致。

## video

在 HTML5 早期的设计中，video 标签跟 img 标签类似，也是使用 src 属性来引入源文件的，不过，我想应该是考虑到了各家浏览器支持的视频格式不同，现在的 video 标签跟 picture 元素一样，也是提倡使用 source 的。

现在的 video 标签可以使用 source 标签来指定接入多个视频源

<video controls="controls" >
  <source src="movie.webm" type="video/webm" >
  <source src="movie.ogg" type="video/ogg" >
  <source src="movie.mp4" type="video/mp4">
  You browser does not support video.
</video>

从这个例子中，我们可以看到，source 标签除了支持 media 之外，还可以使用 type 来区分源文件的使用场景。

video 标签的内容默认会被当做不支持 video 的浏览器显示的内容吗，因此，如果要支持更古老的浏览器，还可以在其中加入 object 或者 embed 标签，这里就不详细展开了。video 中还支持一种标签：track。track 是一种播放时序相关的标签，它最常见的用途就是字幕。track 标签中，必须使用 srclang 来指定语言，此外，track 具有 kind 属性，共有五种。subtitles：就是字幕了，不一定是翻译，也可能是补充性说明。captions：报幕内容，可能包含演职员表等元信息，适合听障人士或者没有打开声音的人了解音频内容。descriptions：视频描述信息，适合视障人士或者没有视频播放功能的终端打开视频时了解视频内容。chapters：用于浏览器视频内容。metadata：给代码提供的元信息，对普通用户不可见。一个完整的 video 标签可能会包含多种 track 和多个 source，这些共同构成了一个视频播放所需的全部信息。

## audio

接下来我们来讲讲 audio，跟 picture 和 video 两种标签一样，audio 也可以使用 source 元素来指定源文件

```js

<audio controls>
  <source src="song.mp3" type="audio/mpeg">
  <source src="song.ogg" type="audio/ogg">
  <p>You browser does not support audio.</p>
</audio>
```

## iframe

这个标签能够嵌入一个完整的网页。不过，在移动端，iframe 受到了相当多的限制，它无法指定大小，里面的内容会被完全平铺到父级页面上。同时很多网页也会通过 http 协议头禁止自己被放入 iframe 中。iframe 标签也是各种安全问题的重灾区。opener、window.name、甚至 css 的 opacity 都是黑客可以利用的漏洞。因此，在 2019 年，当下这个时间点，任何情况下我都不推荐在实际开发中用以前的 iframe。当然，不推荐使用是一回事，因为没人能保证不遇到历史代码，我们还是应该了解一下 iframe 的基本用法：

在新标准中，为 iframe 加入了 sandbox 模式和 srcdoc 属性，这样，给 iframe 带来了一定的新场景。我们来看看例子：

```js

<iframe sandbox srcdoc="<p>Yeah, you can see it <a href="/gallery?mode=cover&amp;amp;page=1">in my gallery</a>."></iframe>
```

这个例子中，使用 srcdoc 属性创建了一个新的文档，嵌入在 iframe 中展示，并且使用了 sandbox 来隔离。这样，这个 iframe 就不涉及任何跨域问题了。