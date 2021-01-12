<template>
	<view>
		<view class="part05-style">
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
		
		<view class="part06-data_mustache">
			<view>数据绑定的学习</view>
			<view>{{msg}}</view>
			<view>{{msg+'2'}}</view>
			<view>{{2+3}}</view>
			<view>{{num1+10}}</view>
			<view>{{flag?'真':'假'}}</view>
		</view>
	
		<view class="part07-v-bind_v-for">
			<button :type="word[inNum]" @click="inChange">v-bind按钮和v-on事件</button>
			<!-- :key标识唯一性，防止添加新标签时复用 -->
			<view v-for="(man,index) in people" :key="index">
				名字：{{man.name}},年龄：{{man.age}},住址：{{man.address}}
			</view>
		</view>
	
		<view class="part08-event">
			<view>事件</view>
			<!-- v-on:语法糖@ -->
			<button size="mini" type="primary" @click="btnClick">按钮</button>
			<button size="mini" type="primary" @click="btn1Click('good',$event)">按钮1</button>
		</view>
	</view>
</template>

<script>
	export default {
		data(){
			return {
				msg:"Hello",
				num1:12,
				flag:true,
				inNum:0,
				word:["default","warn","primary"],
				people: [
					{
						name:"张三",
						age:18,
						address:"上海"
					},
					{
						name:"李四",
						age:19,
						address:"北京"
					},
					{
						name:"王五",
						age:21,
						address:"重庆"
					},
					{
						name:"小明",
						age:20,
						address:"成都"
					}
				]
			}
		},
		methods:{
			inChange() {
				this.inNum=(this.inNum+1)%3
			},
			// 默认没有参数时，这个参数e是事件对象
			btnClick(e) {
				console.log('点击了按钮')
				console.log(e)
			},
			btn1Click(str,e) {
				console.log('点击了按钮1,参数:',str)
				console.log(e)
			}
		}
	}
</script>

<style lang="scss">
	.box1 {
		width: 375rpx;
		height: 375rpx;
		background-color: #ff9f1a;
		font-size: 30rpx;
		color: #ffcccc;
	}

	.tx1 {
		// 使用全局的uni.scss变量
		color: $uni-color-success;
	}
</style>
