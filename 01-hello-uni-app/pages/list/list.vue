<template>
	<view>
		<view>这是list页</view>
		<view style="border: 5rpx #F0AD4E solid;">
			<view class="line">占行文字1</view>
			<view class="line">占行文字2</view>
			<view class="line">占行文字3</view>
			<view class="line">占行文字4</view>
			<view class="line">占行文字5</view>
			<view class="line">占行文字6</view>
			<view class="line">占行文字7</view>
			<view class="line">占行文字8</view>
			<view class="line">占行文字9</view>
			<view class="line">占行文字10</view>
		</view>
		<view v-for="(item,index) in lists" :key="index">
			{{item}}
		</view>
		<!-- 通过按钮调用下拉刷新 -->
		<button @click="pullDown">刷新数据</button>
		
	</view>
</template>

<script>
	export default {
		data() {
			return{
				lists:['Web前端','UI','测试','大数据']
			}
		},
		methods:{
			pullDown(){
				uni.startPullDownRefresh()
			}
		},
		onPullDownRefresh(){
			console.log('触发了下拉刷新')
			// 刷新等操作
			this.lists=['Vuejs','uni-app','Web前端','大数据','UI','测试']
			// 用定时器模拟网络延迟
			setTimeout(function () {
				uni.stopPullDownRefresh();
			}, 1500);
		},
		// 监视滚动条触底
		onReachBottom(){
			console.log('页面触底了')
			// 扩展运算符3个点...展开数组，用逗号隔开
			this.lists = [...this.lists,...['一','二','三','四','五']]
		}
	}
</script>

<style>
	.line{
		line-height: 150rpx;
	}
</style>
