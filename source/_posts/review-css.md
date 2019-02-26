---
title: 前端知识体系回顾-(CSS篇)
categories: 技术
tags:  css
copyright: true
reward: true
date: 2018-10-15 15:30:23
---

# CSS 篇

## 浩瀚星辰，莫忘心记。——Abner <!-- more -->

## 1、CSS选择器

CSS选择器即通过某种规则来匹配相应的标签，并为其设置CSS样式，常用的有类选择器、标签选择器、ID选择器、后代选择器、群组选择器、伪类选择器(before/after)、兄弟选择器(+~)、属性选择器等等。

## 2、CSS Reset
 HTML标签在不设置任何样式的情况下，也会有一个默认的CSS样式，而不同内核浏览器对于这个默认值的设置则不尽相同，这样可能会导致同一套代码在不同浏览器上的显示效果不一致，而出现兼容性问题。因此，在初始化时，需要对常用标签的样式进行初始化，使其默认样式统一，这就是CSS Reset ，即CSS样式重置，比如：*{margin:0,padding:0} 就是最简单CSS Reset， 关于CSS重置请参考：
Neat.css

##  3、盒子布局

盒子模型是CSS比较重要的一个概念，也是CSS 布局的基石。

常见的盒子模型有块级盒子(block)和行内盒子(inline-block)，与盒子相关的几个属性有：margin、border、padding和content等，这些属性的作用是设置盒子与盒子之间的关系以及盒子与内容之间的关系。其中，只有普通文档流中块级盒子的垂直外边距才会发生合并，而行内盒子、浮动盒子或绝对定位之间的外边距不会合并。另外，box-sizing属性的设置会影响盒子width和height的计算。

##  4、浮动布局

设置元素的 float 属性值为 left或right，就能使该元素脱离普通文档流，向左或向右浮动。一般在做宫格布局时会用到，如果子元素全部设置为浮动，则父元素是塌陷的，这时就需要清除浮动，清除浮动的方法也很多，常用的方法是在元素末尾加空元素设置clear:both，更高级一点的就给父容器设置before/after来模拟一个空元素，还可以直接设置overflow属性为auto/hidden来清除浮动。除浮动可以实现宫格布局，行内盒子(inline-block)和table也可以实现同样的效果。

##  5、定位布局

设置元素的position属性值为 relative/absolute/fixed，就可以使该元素脱离文档流，并以某种参照坐标进行偏移。其中，releave是相对定位，它以自己原来的位置进行偏移，偏移后，原来的空间不会被其他元素占用；absolute是绝对定位，它以离自己最近的定位父容器作为参照进行偏移；为了对某个元素进行定位，常用的方式就是设置父容器的poistion:relative，因为相对定位元素在不设置top 和 left 值时，不会对元素位置产生影响；fixed,即固定定位，它则以浏览器窗口为参照物，PC网页底部悬停的banner一般都可以通过fixed定位来实现，但fixed属性在移动端有兼容性问题，因此不推荐使用，可替代的方案是：绝对定位+内部滚动。

##  6、弹性布局

弹性布局即Flex布局，定义了flex的容器一个可伸缩容器，首先容器本身会根据容器中的元素动态设置自身大小；然后当Flex容器被应用一个大小时（width和height），将会自动调整容器中的元素适应新大小。Flex容器也可以设置伸缩比例和固定宽度，还可以设置容器中元素的排列方向（横向和纵向）和是否支持元素的自动换行。有了这个神器，做页面布局的可以方便很多了。注意，设为Flex布局以后，子元素的float、clear和vertical-align属性将失效。

##  7、CSS3 动画

CSS3中规范引入了两种动画，分别是 transition 和 animation，transition可以让元素的CSS属性值的变化在一段时间内平滑的过渡，形成动画效果，为了使元素的变换更加丰富多彩，CSS3还引入了transfrom属性，它可以通过对元素进行 平移(translate)、旋转(rotate)、放大缩小(scale)、倾斜(skew)等操作，来实现2D和3D变换效果。transiton 还有一个结束事件transitionEnd，该事件是在CSS完成过渡后触发，如果过渡在完成之前被移除，则不会触发transitionEnd 。animation 需要设置一个@keyframes，来定义元素以哪种形式进行变换，然后再通过动画函数让这种变换平滑的进行，从而达到动画效果，动画可以被设置为永久循环演示。设置 animation-play-state:paused可以暂停动画，设置 animation-fill-mode:forwards可以让动画完成后定格在最后一帧。另外，还可以通过JS监听animation的开始、结束和重复播放时的状态，分别对应三个事件，即animationStart、animationEnd、animationIteration 。注意，当播放次数设置为1时不会触animationIteration 。和 transition相比，animation 设置动画效果更灵活更丰富，还有一个区别是：transition只能通过主动改变元素的css值才能触发动画效果，而animation一旦被应用，就开始执行动画。另外，HTML5 还新增了一个动画API，即requestAnimationFrame，它通过JS来调用，并按照屏幕的绘制频率来改变元素的CSS属性，从而达到动画效果。

## 8、BFC

BFC是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面元素。比如：内部滚动就是一个BFC，当一个父容器的overflow-y设置为auto时，并且子容器的长度大于父容器时，就会出现内部滚动，无论内部的元素怎么滚动，都不会影响父容器以外的布局，这个父容器的渲染区域就叫BFC。满足下列条件之一就可触发BFC：

根元素，即HTML元素

float的值不为none

overflow的值不为visible

display的值为inline-block、table-cell、table-caption

position的值为absolute或fixed

## 9、Sprite，Iconfont，@font-face

对于大型站点，为了减少http请求的次数，一般会将常用的小图标排到一个大图中，页面加载时只需请求一次网络，然后在css中通过设置background-position来控制显示所需要的小图标，这就是Sprite图。

Iconfont，即字体图标，就是将常用的图标转化为字体资源存在文件中，通过在CSS中引用该字体文件，然后可以直接用控制字体的css属性来设置图标的样式，字体图标的好处是节省网络请求、其大小不受屏幕分辨率的影响，并且可以任意修改图标的颜色。@font-face是CSS3中的一个模块，通过@font-face可以定义一种全新的字体，然后就可以通过css属性font-family来使用这个字体了，即使操作系统没有安装这种字体，网页上也会正常显示出来。

## 10、CSS Hack

早期，不同内核浏览器对CSS属性的解析存在着差异，导致显示效果不一致，比如 margin属性在ie6中显示的距离会比其他浏览器中显示的距离宽2倍，也就是说margin-left:20px;在ie6中距左侧元素的实际显示距离是40px，而在非ie6的浏览器上显示正常。因此，如果要想让所有浏览器中都显示是20px的宽度，就需要在CSS样式中加入一些特殊的符号，让不同的浏览器识别不同的符号，以达到应用不同的CSS样式的目的，这种方式就是css hack， 对于ie6中的margin应用hack就会变成这样：.el {margin-left:20px;_margin-left:10px} 。
兼容各大浏览器的 css hack 如下：
![image](http://upload-images.jianshu.io/upload_images/13702193-5c9f2ca4c257509a?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

下期带来js篇。敬请期待！！!




作者 [@Abner][3]     
[3]: https://www.jianshu.com/p/7f42d52039c4

