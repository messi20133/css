# css基础知识分享

---

### 1. 定义
层叠样式表(英文全称：Cascading Style Sheets)是一种用来表现HTML（标准通用标记语言的一个应用）或XML（标准通用标记语言的一个子集）等文件样式的计算机语言。

### 2. 为文档添加样式的三种方法
* ####行内样式

	`<p style='font-size: 12px'> this is a paragraph </p>`

* ####嵌入样式
	
	`
	<style type="text/css">
		p {font-size: 12px}
	</style>
	`
	
* ####链接样式
	
	`<link href='style.css' rel='stylesheet' type='text/css'/>`
	
### 3.样式来源

* 浏览器默认样式表
* 用户样式表
* 作者链接样式表
* 作者嵌入样式表
* 作者行内样式表 

### 4.权重计算

对每个选择符都按照I-C-E公式计算，
具体方法如下：选择符中有一个Id,就在I的位置上加1， 选择符中有一个class,就在C的位置上加1，选择符中有一个元素名，就在E的位置上加1。

	p       					0-0-1  		权重1
	p.largetext 				0-1-1 		权重 11
	p#largetext 				1-0-1		权重101
	body  p#largetext 			1-0-2		权重102
	body p#largetext ul.mylist  1-1-3		权重114
	
权重相同的情况， 顺序决定权重， 位置最靠下的胜出。
	
	
### 5.选择符
1. __最基础的选择符__

	* 多个声明包含在一条规则里  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     [example](https://codepen.io/messi20133/pen/NgPvBr)
	
	* 多个选择符组合在一起 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     [example](https://codepen.io/messi20133/pen/NgPvBr)
	

2. __上下文选择器__
	*  标签1 &nbsp;&nbsp; 标签2 {声明}  &nbsp;&nbsp; 用于选择作为指定祖先元素后代的标签(注意： 是以空格为分割)  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [example](https://codepen.io/messi20133/pen/GEgMKJ) 
	* 标签1  >  标签2 &nbsp;&nbsp;标签1必须是标签2的父元素， 并且 标签1不能是标签2的父元素之外的其他祖先元素。  
	* 标签1 + 标签2 &nbsp;&nbsp; 紧邻同胞选择符+，标签2必须是紧跟在其同胞标签1的后面。
	* 标签1 ~ 标签2 &nbsp;&nbsp; 一般同胞选择符~， 标签2在其同胞标签1的后面（不一定是紧跟）
	* 通用选择符 * 匹配任何元素。
	
3. __ID和类选择器__
	不用考虑文档层次，直接选中文档中特定的内容。
	
	* 类属性 . 类名
	* 标签带类选择器
	* 多类选择符  可以元素添加多个类
	* ID属性

	什么时候用ID,什么时候用类？
	共同点： 都用于在标记中标识特定标签的html属性，似乎是完全可以相互取代。
	不同点：就css而言，唯一不同的地方就是权重问题，除此之外， id是唯一标识，class表示当前元素属于哪一类，另外，id还有页面锚点的作用。
	
4. __属性选择器__
	
	* 属性名选择符 &nbsp;&nbsp;  标签名[属性名]

	* 属性值选择符 &nbsp;&nbsp;  标签名[属性名=‘属性值’]

5. __伪类选择符__
	* UI伪类  &nbsp;&nbsp;  例如 a:hover , input:focus 
	* 结构化伪类 &nbsp;&nbsp; 例如 div: first-child , div:nth-child(n)
	* 伪元素 &nbsp;&nbsp; 例如 p::first-letter , p::first-line , div::before

### 6.元素类型

##### 块级元素

独占一行， 默认情况下，其宽度自动填满父元素的宽度。 （display: block）典型的块级元素包括div, p, form, ul, li  

#### 行内元素
不会独占一行，相邻行内元素会排列在同一行里， 直到一行放不下了才会换行，其宽度随内容的宽度变化。（display: inline）典型的行内元素包括 span, strong , em

### 7.盒模型
*理解了盒子模型才能更好的排版！！！！！*

在一个文档中，每个元素都被表示为一个矩形的盒子。

在CSS中，使用标准盒模型描述这些矩形盒子中的每一个。这个模型描述了元素所占空间的内容。每个盒子有四个基本属性：外边距, 边框, 内填充边距, 内容。 

![](https://raw.githubusercontent.com/messi20133/css/master/imgs/box.JPG)

标准盒模型的范围包括margin 、border、 padding 、content 四部分， 内容宽度就等于content。

#### 外边距
用空白区域扩展边框区域,分开相邻元素。需要注意外边距合并问题。

#### 边框
包含边框的区域，扩展了内边距区域，位于边框边界内部

#### 内边距
边框到内容的距离，如果内容区域设置了背景颜色或者图片将会延伸到padding上

#### box-sizing 属性
更改用于计算元素高度和宽度的默认盒模型，默认值是content-box

其他取值： border-box 

[example](https://codepen.io/messi20133/pen/VWjMEd)

### 8. 定位

##### static

static 是默认值。任意 position: static; 的元素不会被特殊的定位。一个 static 元素表示它不会被“positioned”，一个 position 属性被设置为其他值的元素表示它会被“positioned”。

##### relative

relative 表现的和 static 一样，除非你添加了一些额外的属性。在一个相对定位（position属性的值为relative）的元素上设置 top 、 right 、 bottom 和 left 属性会使其偏离其正常位置。其他的元素的位置则不会受该元素的影响发生位置改变来弥补它偏离后剩下的空隙。

#### absolute
元素相对于最近的“positioned”祖先元素定位 。如果绝对定位（position属性的值为absolute）的元素没有“positioned”祖先元素，那么它是相对于文档的 body 元素，并且它会随着页面滚动而移动。记住一个“positioned”元素是指 position 值不是 static 的元素。

[example](https://codepen.io/messi20133/pen/OgXBWB)

### 9.布局

利用上面的一些知识做一个三栏布局（三栏， 左中右， 左右固定宽度， 中间自适应）



