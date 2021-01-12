<template>
	<view>
		<view>uni的样式学习</view>
		<view class="box1">box</view>
		<!-- 通过iconfont官网下载字体图标样式 -->
		<view class="iconfont icon-picture"></view>
		<view class="iconfont icon-camera"></view>
		<view class="iconfont icon-time"></view>
		<view class="">
			<text class="tx1">scss样式文字</text>
		</view>
	</view>
</template>

<script>
</script>

<style lang="scss">
	.box1{
		width: 375rpx;
		height: 375rpx;
		background-color:#ff9f1a ;
		font-size: 30rpx;
		color:#ffcccc ;
	}
	.tx1{
		// 使用全局的uni.scss变量
		color: $uni-color-success;
	}
</style>
