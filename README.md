# fullpage 学习文档

---
### 简介
`fullpage.js`是一个基于jQuery的全屏滚动插件，它能够很方便、很轻松的制作出全屏网站。

![fullpage.js](http://www.uedsc.com/wp-content/uploads/2014/06/77.png)

### 主要功能

- 支持鼠标滚动
- 支持前进后退和键盘控制
- 多个回调函数
- 支持手机、平板触摸事件
- 支持CSS3动画
- 支持窗口缩放
- 窗口缩放时自动调整
- 可设置滚动宽度、背景颜色、滚动速度、循环选项、回调、文本对齐方式等等

###兼容性

fullpage.js支持IE8+及其它主流浏览器

###使用方法

####1.引入文件

```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/fullPage.js/2.7.6/jquery.fullPage.css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.0.0-alpha1/jquery.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/fullPage.js/2.7.6/jquery.fullPage.js"></script>
```
通过引用cdnjs网站静态资源库中的jquery.js 和jquery.fullpage.js，（好像可以减轻自己服务器的负担）

####2.HTML
```
<div id="fullpage">
		<div class="section">this is the 1st page</div>
		<div class="section">
			<div class="slide">slide1</div>
			<div class="slide">slide2</div>
			<div class="slide">slide3</div>
			<div class="slide">slide4</div>
		</div>
		<div class="section">this is the 3rd page</div>
		<div class="section">this is the 4th page</div>
	</div>
```
#### 3.javascript
激活fullpage
```
<script>
	$(document).ready(function() {
		$('#fullpage').fullpage({
			navigation: true,
			sectionsColor: ['#6E97B6','#446535','#BFC3C4','#11457C'],
		});
	});
	</script>
```

###配置
####1.选项

| 选项 | 类型 | 默认值 | 说明 |
| ---- | ---- | ------ | ---- |
| verticalCentered | 字符串 | true | 内容是否垂直居中 |
| resize | 布尔值 | false | 字体是否随着窗口缩放而缩放 |
| slidesColor | 函数 | 无 | 设置背景颜色 |
| anchors | 数组 | 无 | 定义锚链接 |
| scrollingSpeed | 整数 | 700 | 滚动速度，单位为毫秒 |
| easing | 字符串 | easeInQuart | 滚动动画方式 |
| menu | 布尔值 | false | 绑定菜单，设定的相关属性与anchors的值对应后，菜单可以控制滚动 |
| navigation | 布尔值 | false | 是否显示项目导航 |
| navigationPosition | 布尔值 | right | 项目导航的位置，可选left或right |
| navigationColor | 字符串 | #000 | 项目导航的颜色 |
| navigationTooltips | 数组 | 空 | 项目导航的tip |
| slidesNavigation | 布尔值 | false | 是否显示左右滑块的项目导航 |
| slidesNavPosition | 布尔值 | bottom | 左右滑块项目导航的位置，可选top或bottom |
| controlArrowColor | 字符串 | #fff | 左右滑块箭头的背景颜色 |
| loopBottom | 布尔值 | false | 滚动到最底部后是否滚回顶部 |
| loopTop | 布尔值 | false | 滚动到最顶部后是否滚底部 |
| loopHorizontal | 布尔值 | true | 左右滑块是否循环滑动 |
| autoScrolling | 布尔值 | true | 是否使用插件的滚动方式，如果选择false，则会出现浏览器自带的滚动条 |
| scrollOverflow | 布尔值 | false | 内容超过满屏后是否显示滚动条 |
| css3 | 布尔值 | false | 是否使用CSS3 transforms滚动 |
| paddingTop | 字符串 | 0 | 与顶部的距离 |
| paddingBottom | 字符串 | 0 | 与底部距离 |
| fixedElement | 字符串 | 无 | null |
| normalScrollElement | null | 无 | null |
| keyboardScroll | 布尔值 | true | 是否使用键盘方向键导航 |
| touchSensitivity | 整数 | 5 | null |
| continuousVertical | 布尔值 | false | 是否循环滚动，与loopTop及loopBottom不兼容 |
| animateAnchor | 布尔值 | true | null |

####2.方法

| **名称** | **说明** |
| -------- | -------- |
| moveSectionUp() | 向上滚动 |
| moveSectionDown() | 向下滚动 |
| moveTo(section,slide) | 滚动到 |
| moveSlideRight() | slide向右滚动 |
| moveSlideLeft() | slide向左滚动 |
| setAutoScrolling() | 设置页面滚动方式，设置为true时自动滚动 |
| setAllowScrolling() | 添加或删除鼠标滚轮/触控板控制 |
| setKeyboardScrolling() | 添加或删除键盘方向键控制 |
| setScrollingSpeed() | 定义以毫秒为单位的滚动速度 |

####3.回调函数

`afterLoad`
滚动到某一屏后的回调函数，接受anchorLink和index两个参数，anchorLink是锚链接的名称，index是序号，从1开始计算

`onLeave`
滚动前的回调函数，接收index、nextIndex和direction3个参数：

 - index是离开的“页面”的序号，从1开始计算；nextIndex是滚动到的“页面”的序号，从1开始计算；direction判断网上滚动还是往下滚动，值是up或down
 - nextIndex是滚动到的“页面”的序号，从1开始计算
 - direction判断往上滚动还是往下滚动，值是up或down
 
`afterRender`
页面结构生成后的回调函数，或者说页面初始化完成后的回调函数

`afterSlideLoad`
滚动到某一水平滑块后的回调函数，与afterLoad类似，接受anchorLink、index、slideIndex、direction4个参数

`onSlideLeave`
某一水平滑块滚动前的回调函数，与onLeave类似，接收anchorLink、index、slideIndex、direction4个参数
