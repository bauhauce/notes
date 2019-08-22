## 总结

- 路由设计
	前进刷新，返回不刷新

- 通用样式封装
	样式reset
	字体
	文字超出情况
	boxsizing border-box
	tap-highlight-color transparent 清除轻触颜色
	-webkit-tap-highlight-color
	-webkit-overflow-scrolling touch 修复iOS滚动生硬

	选中颜色，阴影
	input,textarea 清除样式

- axios封装
	设置请求头，携带登录token
	跨域解决
	请求超时
	请求拦截，跳转登录页

- 登录状态判断

- 图片上传
	input框设置 type="file"
	监听change事件，通过该元素的files[0]属性，拿到文件信息
	将文件信息转成 formData对象，然后添加到Post参数中

- 信息弹窗设计

- 下拉列表

- 上拉刷新

- 下拉加载

- tab页

- 过渡动画

- 支付宝支付

- loading页设计

- 浏览器判断

- 微信登录，微信支付


## 问题

- iOS 滚动问题
	全局滚动和局部滚动
	滚动穿透
	滚动卡顿
	描述：iOS页面存在全局滚动，即整个页面上拉或下拉时会有回弹效果（页面内容未超出没有滚动时也会）； 当页面中元素里的内容超出元素宽高时，会正常产生局部滚动，但是当该元素内容滚到元素顶部或底部时，iOS会认为没有内容可滚动时会变成全局滚动，然后该元素中的内容就无法滚动；
	解决：监听该元素的touchstart/touchmove事件，或者监听该元素的scroll事件，当该元素的scrollTop为0（滚动到顶部）或者该元素的scrollTop + offsetHeight >= scrollHeight时，让该元素scrollTo(0, 1)或者（0, scrollHeight-offsetHeight-1）

- iOS fixed 定位抖动
	描述：页面为fixed定位，且页面内容是可以滚动时，页面中也是fixed定位的元素在页面滚动时会产生抖动；

- iOS 微信网页下input框和fixed定位错位问题 
	描述：input框输入完成，键盘回落后，页面上的fixed定位会错位，导致无法点击到；
	解决：input失焦后，执行window.scrollTo(0, 0),恢复页面定位；

- iOS 上传图片角度问题
	描述：ios上传图片时，如果上传的是ios相机竖拍的照片会变成横放；
	解决：
		1 使用exif-js 获取图片的旋转角度
		2 使用canvas 旋转角度，返回base64格式的文件
		3 将格式转换为blob，再转换为file，添加到formData，然后上传

- 支付宝支付结束后的回调

- 