<script>
	export default {
		// app初始化完成时触发（全局只触发一次）
		onLaunch: function() {
			console.log('App Launch')
		},
		// 从后台进入前台显示
		onShow: function() {
			console.log('App Show')
		},
		// 从前台进入后台
		onHide: function() {
			console.log('App Hide')
		},
		// 报错时触发
		onError:function(){
			console.log('App Error')
		}
	}
</script>

<style>
	/*每个页面公共css */
	@import url("./static/fonts/iconfont.css");
</style>
