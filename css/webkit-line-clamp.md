# -webkit-line-clamp
## 概述
-webkit-line-clamp 是一个 不规范的属性（unsupported WebKit property），它没有出现在 CSS 规范草案中。
限制在一个块元素显示的文本的行数。 为了实现该效果，它需要组合其他外来的WebKit属性。常见结合属性：
display: -webkit-box; 必须结合的属性 ，将对象作为弹性伸缩盒子模型显示 。
-webkit-box-orient 必须结合的属性 ，设置或检索伸缩盒对象的子元素的排列方式 。
text-overflow，可以用来多行文本的情况下，用省略号“...”隐藏超出范围的文本 。
## 语法
-webkit-line-clamp：\<number\>
默认值： ?  *?表示不清楚*
适用于：块元素
继承性：无
动画性：否
计算值：指定的值
## 取值
\<number\>:块元素显示的文本的行数。
*CSS3新增属性可能存在描述错误及变更，仅供参考，持续更新*
## 兼容性
![](/images/1.png)
*?表示不清楚*
## 示例
	<!DOCTYPE HTML>
	<html>
	<head>
	    <meta charset="utf-8">
	    <title>示例</title>
	</head>
	<body>
	<p style="overflow : hidden;text-overflow: ellipsis;display: -webkit-box; webkit-line-clamp: 2;-webkit-box-orient: vertical;">
	 static：对象遵循常规流。top，right，bottom，left等属性不会被应用。 relative： 对象遵循常规流，并且参照自身在常规流中的位置通过top，right，bottom，left属性进行偏移时不影响常规流中的任何元素。 absolute：对象脱离常规流，使用top，right，bottom，left等属性进行绝对定位，盒子的偏移位置不影响常规流中的任何元素，其margin不与其他任何margin折叠。fixed：对象脱离常规流，使用top，right，bottom，left等属性以窗口为参考点进行定位，当出现滚动条时，对象不会随着滚动。center：对象脱离常规流，使用top，right，bottom，left等属性指定盒子的位置或尺寸大小。盒子在其包含容器垂直水平居中。盒子的偏移位置不影响常规流中的任何元素，其margin不与其他任何margin折叠。（CSS3）page：盒子的位置计算参照absolute。盒子在分页媒体或者区域块内，盒子的包含块始终是初始包含块，否则取决于每个absolute模式。（CSS3） sticky： 对象在常态时遵循常规流。它就像是 relative 和 fixed 的合体，当在屏幕中时按常规流排版，当卷动到屏幕外时则表现如fixed。该属性的表现是现实中你见到的吸附效果。（CSS3）* CSS3新增属性可能存在描述错误及变更，仅供参考，持续更新
	</p>
	</body>
	</html>
