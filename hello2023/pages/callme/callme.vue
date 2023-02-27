<template>
	<view class="box-item">
		<view>联系我们</view>
		<button @click="setStorage">存储数据</button>
		<button @click="getStorage">获取数据</button>
		<view v-for="item in list">{{item}}</view>
		<!-- <button @click="pullDown">下拉刷新</button> -->
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:['小王','小李','小红','小王','小李','小红','小王','小李','小红']
			}
		},
		onPullDownRefresh() {
			console.log('触发了下拉刷新')
			setTimeout(()=>{
				this.list = ['小陈','小李','小红','小王','小李','小红','小王','小李','小红']
				uni.stopPullDownRefresh()
			},2000)
		
		},
		onReachBottom() {
			console.log('页面触底了')
			this.list = [...this.list,...['陈','李','红','王']]
			
		},
		methods:{
			pullDown(){
				uni.startPullDownRefresh()
			},
			setStorage(){
				uni.setStorage({
					key:'id',
					data:800,
					success() {
						console.log('存储成功')
					}
				})
			},
			getStorage(){
				uni.getStorage({
					key:"id",
					success(res) {
						console.log('获取成功',res)
					}
				})
			}
		}
	}
</script>

<style>
	.box-item{
		height: 100px;
		line-height: 100px;
	}
</style>
