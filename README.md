# LearnUniAppPart01
学习uni-app框架  
uni-app 是一个使用 Vue.js 开发所有前端应用的框架，开发者编写一套代码，可发布到iOS、Android、Web（响应式）、以及各种小程序（微信/支付宝/百度/头条/QQ/钉钉/淘宝）、快应用等多个平台。 

# 一、资料来源
（B站Up主**玩儿派**转载自 杭州校区黑马程序员**刘老师**）  
(1-p)B站视频：https://www.bilibili.com/video/BV1CC4y1476y?p=1

# 二、知识总结大纲
(数字表示视频分P)
## 一、uni-app的简介和基本使用 (1-5)
### 1.1 uni-app的简介
* uni-app官方文档URL：https://uniapp.dcloud.io/README
* uni-app 是一个使用 **Vue.js** 开发所有前端应用的框架，开发者编写一套代码，`可发布到iOS、Android、Web（响应式）、以及各种小程序（微信/支付宝/百度/头条/QQ/钉钉/淘宝）、快应用等多个平台`。 
### 1.2 为什么要选择uni-app
主要特点和优势：  
1. 开发者/案例数量更多
2. 平台能力不受限
3. 性能体验优秀
4. 周边生态丰富
5. 学习成本低
6. 开发成本低
### 1.3 搭建uni-app环境
* 安装编辑器HBuilderX：https://www.dcloud.io/hbuilderx.html
* 安装微信开发者工具：https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html
* 除此之外，可以下载模拟器等
### 1.4 创建和运行uni-app项目
* 打开HBuilderX程序，新建项目，选择uni-app(默认模板)
* 运行项目(各种平台)，运行解决方法：https://uniapp.dcloud.io/quickstart
  * Chrome运行
  * 微信开发者工具运行(微信小程序)-第一次运行时：要在编辑器运行配置里填**工具路径**，然后**打开并登陆**工具的端口
  * 手机或模拟器：模打开拟器在所在目录使用指令：`adb devices`查看开放端口号，然后填入编辑器的运行端口.手机方式略.
### 1.5 项目目录介绍
官方介绍URL：https://uniapp.dcloud.io/frame?id=%e5%bc%80%e5%8f%91%e8%a7%84%e8%8c%83  
一个uni-app工程，默认包含如下目录及文件：  
```
┌─pages                 业务页面文件存放的目录
│  └─index
│     └─index.vue       index页面
├─static                存放应用引用静态资源（如图片、视频等）的目录，注意：静态资源只能存放于此
├─App.vue               应用配置，用来配置App全局样式以及监听 应用生命周期
├─main.js               Vue初始化入口文件
├─manifest.json         配置应用名称、appid、logo、版本等打包信息等
├─pages.json            配置页面路由、导航条、选项卡等页面类信息等
└─uni.scss              uni-app内置的常用样式变量
```
### 1.6 uni-app开发规范
1. Vue单文件组件 (SFC) 规范：https://vue-loader.vuejs.org/zh/spec.html
2. uni-app组件规范：https://uniapp.dcloud.io/component/README
3. 接口能力(JS API) 靠近微信小程序规范，但前缀将`wx`改为`uni`.uni-app接口规范：https://uniapp.dcloud.io/api/README
4. 数据绑定及事件处理同 Vue.js 规范，同时补充了**App及页面的生命周期**
5. 为兼容多端运行，建议使用**flex布局**进行开发
### 1.7 配置pages.json
官方的pages.json配置介绍URL：https://uniapp.dcloud.io/collocation/pages  
* pages页面属性
* globalStyle全局属性
### 1.8 创建并配置页面
* 在pages文件夹里新建页面文件夹和页面vue文件
* 在pages.json里新建`page对象`，再配置`path属性`，默认第一个为主页.
```JSON
"pages": [ 
	{
		"path": "pages/index/index",
		"style": {
				"navigationBarTitleText": "App标题"
		}
	},
	{
		"path": "pages/message/message",
		"style": {
			"navigationBarTitleText": "信息标题"
		}
	}
]
```
## 二、uniapp的界面设计 (6-8)
### 2.1 导航栏tabbar
* **tabBar**是pages.json里的一个根属性，封装的一个导航栏组件.
  * 包括一个`list数组`，color/selectColor 2种文字颜色等属性.
  * list数组包括多个tab对象，`最少2个、最多5个tab`!
  * 一个tab对象包括页面路径、2个图标(未选中,选中)、文字
* 使用如下：
```JSON
"tabBar": {
  "color":"#000000",
	"selectedColor":"#f39c12",
	"list": [
			{
			"text":"首页",
			"pagePath":"pages/index/index",
			"iconPath":"static/tabs/home.png",
			"selectedIconPath":"static/tabs/home_active.png"
		},
		{
  		"text":"信息",
			"pagePath":"pages/message/message",
			"iconPath":"static/tabs/survey.png",
			"selectedIconPath":"static/tabs/survey_active.png"
		},
		{
			"text":"我的",
			"pagePath":"pages/profile/profile",
			"iconPath":"static/tabs/user.png",
			"selectedIconPath":"static/tabs/user_active.png"
		}
	]
}
```
* 注意：tabBar的`"position":"top"`属性仅支持微信小程序!
### 2.2 启动模式配置condition
* 启动模式配置，仅开发期间生效，用于模拟直达页面的场景，如：小程序转发后，用户点击所打开的页面。
```JSON
"condition": {
		"current": 0,
		"list": [
			{
				"name":"详情页面",
				"path":"pages/detail/detail",
				"query":"id=80"
			}
		]
	}
```
## 三、组件的基本使用 (9-)
* uni-app提供了非常丰富的组件，组件-官方文档URL：https://uniapp.dcloud.io/component/README
组件分类主要有：
* [视图容器](https://uniapp.dcloud.io/component/view)
* [基础内容](https://uniapp.dcloud.io/component/icon)
* [表单组件](https://uniapp.dcloud.io/component/button)
* [路由与页面跳转](https://uniapp.dcloud.io/component/navigator)
* [媒体组件](https://uniapp.dcloud.io/component/audio)
* [地图](https://uniapp.dcloud.io/component/map)
* [画布](https://uniapp.dcloud.io/component/canvas)
* [webview](https://uniapp.dcloud.io/component/web-view)
* [广告](https://uniapp.dcloud.io/component/ad)
* [导航类组件](https://uniapp.dcloud.io/component/navigation-bar)
* [页面属性配置节点](https://uniapp.dcloud.io/component/page-meta)
* [小程序开放能力组件](https://uniapp.dcloud.io/component/official-account)
* [App_nvue专用组件](https://uniapp.dcloud.io/component/barcode)
* [扩展组件（uni_ui）](https://uniapp.dcloud.io/component/README?id=uniui)
* [uniCloud组件](https://uniapp.dcloud.io/uniCloud/unicloud-db)
* [datacom组件规范](https://uniapp.dcloud.io/component/datacom)
* [配置小程序插件](https://uniapp.dcloud.io/component/mp-weixin-plugin)
* [原生组件说明](https://uniapp.dcloud.io/component/native-component)
### 3.1 text文本组件
* selectable文本是否可选、space	显示连续空格、decode是否解码
  * ensp	中文字符空格一半大小
  * emsp	中文字符空格大小
  * nbsp	根据字体设置的空格大小
### 3.2 view视图容器
* 它类似于传统html中的div，用于包裹各种元素内容。
* hover-class属性：指定按下去的`样式类`。当 hover-class="none" 时，没有点击态效果
* hover-stop-propagation属性：在嵌套内的view使用，false时阻止冒泡
* :hover-stay-time延长效果时间，毫秒数字
* :hover-start-time延迟出现效果时间，毫秒数字
### 3.3 button按钮组件
* size尺寸：default、mini
* type样式：primary、default、warn
  * primary：微信小程序、360小程序为绿色，App、H5、百度小程序、支付宝小程序、快应用为蓝色，字节跳动小程序为红色，QQ小程序为浅蓝色。如想在多端统一颜色，请改用default，然后自行写样式.
  * default：白色
  * warn：红色
* loading: 前面添加一个加载图标
### 3.4 image图片组件
* src属性：支持本地和在线图片
* mode：有13种模式
	* scaleToFill	不保持纵横比缩放图片，使图片的宽高完全拉伸至填满 image 元素
	* aspectFit	保持纵横比缩放图片，使图片的长边能完全显示出来。
	* aspectFill	保持纵横比缩放图片，只保证图片的短边能完全显示出来。
	* widthFix	宽度不变，高度自动变化，保持原图宽高比不变
	* heightFix	高度不变，宽度自动变化，保持原图宽高比不变
	### 3.5 uni的样式和scss和字体图标