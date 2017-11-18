# 绝对长度单位

|英寸|厘米|毫米|磅|pc|
|-|-|-|-|-|
|inch|cm|mm|pt|pica|

# 相对长度单位

是网页设计中使用最多的长度单位，包括`px、em、rem`等

# 屏幕尺寸

![image](https://user-images.githubusercontent.com/17243165/32698819-74cb03ca-c7e6-11e7-817f-408337368032.png)



> 指屏幕的对角线的长度，单位是英寸，1英寸=2.54厘米

|iPhone 4/4S|iPhone 5/5C/5S/SE|iPhone 6/6S|iPhone 6S Plus|iPhone 7|iPhone 7 Plus|iPhone 8|iPhone 8 Plus|iPhone X|
|-|-|-|-|-|-|-|-|-|
|3.5英寸|4英寸|4.7英寸|5.5英寸|4.7英寸|5.5英寸|4.7英寸|5.5英寸|5.8英寸|

# 屏幕分辨率

指在横纵向上的像素点数，单位是**px**，1px=1个像素点。一般以`纵向像素*横向像素`来表示一个手机的分辨率，如1960*1080（这里的1像素指的是物理设备的1个像素点）

|机型|分辨率|机型|分辨率|机型|分辨率|
|-|-|-|-|-|-|
|iPhone 4/4S|960*640|iPhone 6S Plus|1920*1080|iPhone 8 Plus|1920*1080|
|iPhone 5/5S|1136*640|iPhone 7|1334*750|iPhone X|2436*1125|
|iPhone SE|1136*640|iPhone 7 Plus|1920*1080|||
|iPhone 6/6S|1334*750|iPhone 8|1334*750|||

# 屏幕像素密度

![image](https://user-images.githubusercontent.com/17243165/32698749-8733c61a-c7e5-11e7-8e89-6f7198f26e25.png)

屏幕上每英寸可以显示的像素点的数量，单位是**ppi**，即**pixels per inch**的缩写。屏幕像素密度与屏幕尺寸和屏幕分辨率有关，在单一变化条件下，屏幕尺寸越小、分辨率越高，像素密度越大，反之越小


![image](https://user-images.githubusercontent.com/17243165/32697840-3ad2f360-c7d4-11e7-9c99-de829a35da6e.png)

- 屏幕上勾股定理算出对角线的分辨率：**√(1920²+1080²)≈2203px**
- 对角线分辨率除以屏幕尺寸：**2203/5≈440dpi**

```js
1920^2 + 1080^2 ≈ 2203^2  //3686400 + 1166400 = 4852800
2203 / 5 ≈ 440
```

# PPI与DPI

![image](https://user-images.githubusercontent.com/17243165/32707813-70d66130-c861-11e7-9dec-04eb87490448.png)

PPI（Pixel Per Inch by diagonal）：表示沿着对角线，每英寸所拥有的像素（Pixel）数目
PPI数值越高，代表显示屏能够以越高的密度显示图像，即通常所说的分辨率越高、颗粒感越弱

|ppi与dpi|描述|
|-|-|
|ppi|`pixels per inch`，屏幕上每英寸可以显示的像素点的数量，即屏幕像素密度|
|dpi|`dots per inch`，最初用于衡量打印物上每英寸的点数密度，就是打印机可以在一英寸内打多少个点。当dpi的概念用在计算机屏幕上时，就称之为ppi。ppi和dpi是同一个概念，Android比较喜欢使用dpi，IOS比较喜欢使用ppi|

# Viewport

移动端开发中，通常我们都会采用`meta`标签设置`viewport`
```html
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
```
## viewport是什么?

![image](https://user-images.githubusercontent.com/17243165/32706923-687a642e-c85b-11e7-80f5-17c77624b6ff.png)

通俗来讲，移动端的viewport就是我们所能看到的手机端浏览器的可视窗口大小，但viewport又不仅仅局限于可视窗口的大小，一般情况下，它是比默认窗口大小要大的，这是因为考虑到移动设备的分辨率相对于桌面电脑来说都比较小，所以为了能在移动端正常显示为桌面浏览器而设计的网页，移动端的浏览器都会默认把自己的默认的viewport设为980px到1024px不等，但其后果就是会出现横向滚动条，因为移动端浏览器可视区域的大小是比默认的viewport宽度要小的

|参数|描述|
|-|-|
|width|设置layout viewport的宽度，为一个正整数，或字符串"device-width"|
|initial-scale|设置页面的初始缩放值，为一个数字，可以带小数|
|minimum-scale|允许用户的最小缩放值，为一个数字，可以带小数|
|maximum-scale|允许用户的最大缩放值，为一个数字，可以带小数|
|height|设置layout viewport  的高度，这个属性对我们并不重要，很少使用|
|user-scalable|是否允许用户进行缩放，值为"no"或"yes", no 代表不允许，yes代表允许|

## 不同的设备对1px有不一样的定义

在css中我们一般使用px作为单位，在桌面浏览器中css的1个像素往往都是对应着电脑屏幕的1个物理像素，这可能会造成我们的一个错觉，那就是css中的像素就是设备的物理像素。但实际情况却并非如此，css中的像素只是一个抽象的单位，在不同的设备或不同的环境中，css中的1px所代表的设备物理像素是不同的。在为桌面浏览器设计的网页中，我们无需对这个津津计较，但在移动设备上，必须弄明白这点。在早先的移动设备中，屏幕像素密度都比较低，如iphone3，它的分辨率为320x480，在iphone3上，一个css像素确实是等于一个屏幕物理像素的。后来随着技术的发展，移动设备的屏幕像素密度越来越高，从iphone4开始，苹果公司便推出了所谓的Retina屏，分辨率提高了一倍，变成640x960，但屏幕尺寸却没变化，这就意味着同样大小的屏幕上，像素却多了一倍，这时，一个css像素是等于两个物理像素的。


在移动端浏览器中以及某些桌面浏览器中，window对象有一个devicePixelRatio属性，它的官方的定义为：设备物理像素和设备独立像素的比例，也就是`devicePixelRatio = 物理像素 / 独立像素`。css中的px就可以看做是设备的独立像素，所以通过devicePixelRatio，我们可以知道该设备上一个css像素代表多少个物理像素。例如，在Retina屏的iphone上，devicePixelRatio的值为2，也就是说1个css像素相当于2个物理像素

其实就是移动端和PC端的px是不同的，移动端的屏幕可视区域(viewport)小但像素多，所以跟PC相比的每个独立像素点的物理像素是多的，也就是移动端物理像素更密集，所以更PC的独立像素有`dp`的倍数转换

在进行具体的分析之前，首先得知道下面这些关键性基本概念(术语)。

## 物理像素(physical pixel)

一个物理像素是显示器(手机屏幕)上最小的物理显示单元，在操作系统的调度下，每一个设备像素都有自己的颜色值和亮度值。

## 设备独立像素(density-independent pixel)

设备独立像素(也叫密度无关像素)，可以认为是计算机坐标系统中得一个点，这个点代表一个可以由程序使用的虚拟像素(比如: css像素)，然后由相关系统转换为物理像素。

所以说，物理像素和设备独立像素之间存在着一定的对应关系，这就是接下来要说的设备像素比。

## 设备像素比(device pixel ratio )

设备像素比(简称dpr)定义了物理像素和设备独立像素的对应关系，它的值可以按如下的公式的得到：
```html
设备像素比 = 物理像素 / 设备独立像素 // 在某一方向上，x方向或者y方向
```
还可以通过window.devicePixelRatio获取到当前设备的dpr
```js
window.devicePixelRatio
```

|机型|iPhone 3G/3GS|iPhone 4/4S|iPhone 5/5C/5S/SE|iPhone 6/6S|iPhone 6S Plus|iPhone 7|iPhone 7 Plus|iPhone 8|iPhone 8 Plus|iPhone X|
|-|-|-|-|-|-|-|-|-|-|-|
|屏幕尺寸|3.5英寸|3.5英寸|4英寸|4.7英寸|5.5英寸|4.7英寸|5.5英寸|4.7英寸|5.5英寸|5.8英寸|
|独立像素(CSS像素)|480*320|480*320|568*320|667*375|736*414|||||812*375|
|物理像素(分辨率)|480*320|960*640|1136*640|1334*750|1920*1080(2208x1242)|1334*750|1920*1080|1334*750|1920*1080|2436*1125|
|ppi/dpi(像素密度)|163|326|326|326|401|326|326|326|401|458|
|dpr(倍图)|1|2|2|2|3(2.5)|3|3|3|3|3(2.9)|

如果APP要同时兼容iPhone3GS~iPhone6+，则需要提供icon.png/icon@2x.png/icon@3x.png三种分辨率的图片

在Android中，规定以160dpi为基准，1dp=1px。如果密度是320dpi，则1dp=2px，以此类推

2K分辨率指的是屏幕分辨率达到了一种级别,指屏幕横向像素达到2000以上（iPhone X是2K屏）

# 手淘适配方案

[lib-flexible](https://github.com/amfe/lib-flexible)

# iPhoneX的适配

## background-color

如果网页设置了一个背景颜色，那么最简单解决方案是，在body节点设置`background-color`，使背景颜色填充整个屏幕，从而解决横屏显示左右白边的问题

## viewport-fit
```html
<!--默认值:可视窗口完全包含网页内容 相当于在安全区域展示-->
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=auto">
<!--或-->
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=contain">
<!--网页内容完全覆盖可视窗口-->
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
```

|viewport-fit|描述|示例|示例|示例|
|-|-|-|-|-|
|auto/contain|默认值，页面内容显示在`safe area`内|[示例1](https://wscats.github.io/iPhone-X/viewport-fit/contain/)|||
|cover|页面内容充满屏幕|[示例1](https://wscats.github.io/iPhone-X/viewport-fit/cover/cover.html)|[示例2](https://wscats.github.io/iPhone-X/viewport-fit/cover/sefe-cover.html)|[示例3](https://wscats.github.io/iPhone-X/viewport-fit/min-max/)|
|横屏列表侧刘海|横屏下列表环绕刘海|[示例1](https://wscats.github.io/iPhone-X/css-shape-iphoneX/iPhoneX3.html)|

### 设置auto前
![image](https://user-images.githubusercontent.com/17243165/32718857-6d1c3b0e-c899-11e7-9b70-7bb980cd022d.png)
### 设置cover后
![image](https://user-images.githubusercontent.com/17243165/32718849-6434b66a-c899-11e7-893d-8eb05d2615c6.png)

## safe-area-inset-*

在设置`viewport-fit=cover`之后，Web中会新增四个常量
```css
safe-area-inset-top
safe-area-inset-right
safe-area-inset-left
safe-area-inset-bottom
```
分别表示safe area和可视窗口viewport顶部，右边，左边，底部的间距，可以用于设置margin和padding或者绝对定位时left和top

> 注意：在横屏和竖屏状态下，safe-area-inset-*的值不同

![image](https://user-images.githubusercontent.com/17243165/32719209-85d21f00-c89a-11e7-820c-60c9f15651d4.png)

为了解决应用`viewport-fit=cover`之后，有些显示内容被裁剪的问题，我们可以通过添加边距使得网页主要内容处于safe area中不被裁剪，解决方式如下

```css
padding: constant(safe-area-inset-top) constant(safe-area-inset-right) constant(safe-area-inset-bottom) constant(safe-area-inset-left);
```
![image](https://user-images.githubusercontent.com/17243165/32719362-12474910-c89b-11e7-82a0-6a8a9c7c32d7.png)

示例，比如下面是顶部导航条的适配，能让左上右都能出现padding来让元素保留在安全区域以内
```html
<header>
	<button>返回</button> 头部
</header>
<style media="screen">
	* {
		margin: 0;
		padding: 0;
	}
	body {
		width: 100%;
		height: 100%;
		//设置背景颜色，也是一种适配方案
		background-color: #A4F4B0;
	}
	header {
		background-color: red;
		height: 50px;
		line-height: 50px;
		width: 100%;
		color: white;
		position: fixed;
		left: 0;
		right: 0;
		top: 0;
		bottom: 0px;
		//cover下元素出现对应的padding来适配
		padding-left: constant(safe-area-inset-left);
		padding-right: constant(safe-area-inset-right);
		//padding-bottom: constant(safe-area-inset-bottom);
		padding-top: constant(safe-area-inset-top);
	}
	
	button {
		display: inline-block;
		background-color: blue;
		color: white;
		border: none;
		height: 50px;
		width: 80px;
		//字体记得必须设置，不然按钮会有像素的误差
		font-size: 18px;
	}
</style>
```

# 参考文档

- [移动端高清、多屏适配方案](http://www.html-js.com/article/Mobile-terminal-H5-mobile-terminal-HD-multi-screen-adaptation-scheme%203041)
- [手淘移动端适配的方案学习和相关思考](http://blog.csdn.net/liujie19901217/article/details/51982403)

# iPhone X适配参考文档
- [iPhone X的Web设计](https://www.w3cplus.com/mobile/designing-websites-for-iphone-x.html)
- [剖析 iOS 11 网页适配问题](https://objcer.com/2017/09/21/Understanding-the-WebView-Viewport-in-iOS-11-iPhone-X/)
- [关于H5页面在iPhoneX适配](https://www.cnblogs.com/lolDragon/p/7795174.html)
