# css基础知识分享

1. css基础
3. 定位
4. 页面布局
5. css3新特性

---

## 1.css基础

### 定义
层叠样式表(英文全称：Cascading Style Sheets)是一种用来表现HTML（标准通用标记语言的一个应用）或XML（标准通用标记语言的一个子集）等文件样式的计算机语言。

### 为文档添加样式的三种方法
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
	
	
### 选择符
1. __最基础的选择符__

	* 多个声明包含在一条规则里  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     [example](https://codepen.io/messi20133/pen/NgPvBr)
	
	* 多个选择符组合在一起 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     [example](https://codepen.io/messi20133/pen/NgPvBr)
	

2. __上下文选择器__
	*  标签1 &nbsp;&nbsp; 标签2 {声明}  &nbsp;&nbsp; 用于选择作为指定祖先元素后代的标签(注意： 是以空格为分割)  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [example](https://codepen.io/messi20133/pen/GEgMKJ) 
	* 标签1  >  标签2 &nbsp;&nbsp;标签1必须是标签2的父元素， 并且 标签1不能是标签2的父元素之外的其他祖先元素。&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[example](https://codepen.io/messi20133/pen/ZyWPpa)  
	* 标签1 + 标签2 &nbsp;&nbsp; 紧邻同胞选择符+，标签2必须是紧跟在其同胞标签1的后面。 &nbsp;&nbsp;&nbsp;&nbsp; [example](https://codepen.io/messi20133/pen/jwqJmm)
	* 标签1 ~ 标签2 &nbsp;&nbsp; 一般同胞选择符~， 标签2在其同胞标签1的后面（不一定是紧跟）;&nbsp;&nbsp;&nbsp;&nbsp; [example](https://codepen.io/messi20133/pen/jwqJmm)

	* 通用选择符 * 匹配任何元素。
	
3. __ID和类选择器__
	不用考虑文档层次，直接选中文档中特定的内容。
	
	* 类属性 . 类名

	* 标签带类选择器
	
	* 多类选择符  可以元素添加多个类    [example](https://codepen.io/messi20133/pen/pwyYad)
	
	* ID属性

	什么时候用ID,什么时候用类？
	共同点： 都用于在标记中标识特定标签的html属性，似乎是完全可以相互取代。
	不同点：
4. __属性选择器__

## 4.css3新特性
	
### 4.1新的选择器
:nth-clild()， :not(), :first-child, :last-child, :empty, :checked, :enabled, :disabled
### 4.2边框和颜色
#####透明度
	
	color: rgba(255,0, 0, 0.75)

#####圆角
	border-radius: 15px

[example](https://codepen.io/messi20133/pen/pwyBgO)

####渐变
#####线性渐变
从（x1,y1）到(x2,y2)水平渐变
	
	-webkit-gradient(linear,0% 0%,100% 0%,from(#2A8BBE),to(#FE280E))
从（x1,y1）到(x2,y2)水平渐变,中间有拐点
	
	-webkit-gradient(linear,0% 0%,100% 0%,from(#2A8BBE),
       color-stop(0.33,#AAD010),color-stop(0.33,#FF7F00),to(#FE280E))
#####径向渐变
不是一个点到一个点的渐变， 是一个圆到一个圆的渐变
	
	-webkit-gradient(radial,50 50,50,50 50,0,from(black),color-stop(0.5,red),to(blue));
	
[example]	(https://codepen.io/messi20133/pen/PjNgmJ)

		




