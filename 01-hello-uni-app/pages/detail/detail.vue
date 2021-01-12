<template>
	<view>
		<view>详情页</view>
		<view class="part01-text">
			<view>
				<text selectable>text嵌套的view变块级元素，selectable属性不可选中文字</text>
			</view>
			<view>
				<text selectable>唱歌跳舞打篮球，可以选中</text>
			</view>
			<view>
				<text selectable space="ensp">唱歌 跳舞打篮球</text>
			</view>
			<view>
				<text selectable space="emsp">唱歌 跳舞打篮球</text>
			</view>
			<view>
				<text selectable space="emsp">唱歌&gt; 跳舞打篮球</text>
			</view>
			<view>
				<text selectable space="nbsp" style="font-size: 64upx;">唱歌 跳舞打篮球</text>
			</view>
			<!-- decode 可以解析的有 &nbsp; &lt; &gt; &amp; &apos; &ensp; &emsp;。 -->
		</view>

		<view class="part02-view">
			<!-- hover-class点击效果
		 :hover-stay-time延长效果时间 -->
			<view class="box1" hover-class="box1-active" :hover-stay-time="2500">
				<!-- hover-start-time延迟出现效果时间，需要传入数字，用v-bind -->
				<view class="box" hover-class="box-active" :hover-start-time="2000" hover-stop-propagation>
					这是一个view组件
				</view>
			</view>
		</view>
		
		<view class="part03-button">
			<button size="default">按钮1</button>
			<button size="mini">按钮2</button>
			<button type="primary">按钮3</button>
			<button type="primary" disabled>禁用按钮3</button>
			<button type="default">按钮4</button>
			<button type="warn">按钮5</button>
			<button loading>loading</button>
			页面跳转方式：navigator组件、goto、navigateTo(h5,不跨端)
			<view>
				<!-- <navigator url="../index/index"><button>navigator组件跳转</button></navigator>
				<button @click="goto('../index/index')">自定义方法跳转到</button>
				<button @click="navigateTo('pages/index/index')">navigateTo跳转到</button> --><!-- 这种写法只有h5平台支持，不跨端，不推荐使用 -->
				<button @click="$router.push('../index/index')">跳转</button>
			</view>
		</view>
		
		<view class="part04-image" style="border: 1upx #4CD964 solid;">
			<!-- scaleToFill默认宽度 300px、高度 225px -->
			<image src="http://destiny001.gitee.io/image/cxk.gif"></image>
			<!-- aspectFit长边显示出来 -->
			<image src="http://destiny001.gitee.io/image/cxk.gif" mode="aspectFit"></image>
			<!-- aspectFill短边显示出来 -->
			<image src="http://destiny001.gitee.io/image/cxk.gif" mode="aspectFill"></image>
		</view>
	
	
	</view>
</template>

<script>
</script>

<style>
	.box {
		width: 300upx;
		height: 300upx;
		background-color: #e84393;
	}

	.box1 {
		width: 500upx;
		height: 500upx;
		background-color: #fdcb6e;
	}

	.box-active {
		background-color: #fab1a0;
	}

	.box1-active {
		background-color: #00b894;
	}
</style>
