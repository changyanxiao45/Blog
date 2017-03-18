# 处理移动端 click 事件 300 毫秒延迟
[ github项目地址 ](https://github.com/ftlabs/fastclick "github项目地址")
## 为什么存在延迟？
根据 Google 开发者文档
> ...mobile browsers will wait approximately 300ms from the time that you tap the button to fire the click event. The reason for this is that the browser is waiting to see if you are actually performing a double tap.
从点击屏幕上的元素到触发元素的 click 事件，移动浏览器会有大约 300 毫秒的等待时间。为什么这么设计呢？ 因为它想看看你是不是要进行双击（double tap）操作。
## 兼容性
-Mobile Safari on iOS 3 and upwards
-Chrome on iOS 5 and upwards
-Chrome on Android (ICS)
-Opera Mobile 11.5 and upwards
-Android Browser since Android 2
-PlayBook OS 1 and upwards
## 不应用 FastClick 的场景
-桌面浏览器
-如果 viewport meta 标签 中设置了 width=device-width， Android 上的 Chrome 32+ 会禁用 300ms 延时；
	<meta name="viewport" content="width=device-width, initial-scale=1">
-viewport meta 标签如果设置了 user-scalable=no，Android 上的 Chrome（所有版本）都会禁用 300ms 延迟。
-IE10 中，可以使用 css 属性 -ms-touch-action: none 禁止元素双击缩放
([参考文章]([https://blogs.msdn.microsoft.com/askie/2013/01/06/how-to-implement-the-ms-touch-action-none-property-to-disable-double-tap-zoom-on-windows-touch-devices/ "参考文章"))
## 使用方法
	if ('addEventListener' in document) {
	    document.addEventListener('DOMContentLoaded', function() {
	        FastClick.attach(document.body);
	    }, false);
	}
