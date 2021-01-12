<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<button @click="$router.push('pages/detail/detail')">案例详情</button>
		<button @click="$router.push('pages/uni-style/uni-style')">样式详情</button>
		<button @click="$router.push('pages/list/list')">List详情</button>
		<!-- <navigator url="pages/detail/detail"><button type="default">详情</button></navigator> -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		methods: {

		},
		// onLoad参数为上一个页面的对象数据，这2个触发1次
		onLoad(options) {
			console.log('index页面加载了',options)
		},
		onReady() {
			console.log('页面初次渲染完成')
		},
		// show和hide 会多次触发
		onShow(){
			console.log('页面显示了')
		},
		onHide() {
			console.log('页面隐藏了')
		}
		
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
