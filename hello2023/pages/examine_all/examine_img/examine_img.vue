<template>
	<view>
		<view>图片检测</view>
		<button type="primary"    @click="chooseImg">上传图片</button>
		<image v-for="item in ImgArr" :src="item" @click="previewImg(item)"></image>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				ImgArr:[]
			}
		},
		methods: {
			chooseImg(){
				console.log('上传图片')
				uni.chooseImage({
					count: 6, //默认9
					sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
					sourceType: ['album'], //从相册选择
					// success: function (res) {
					// 	console.log(JSON.stringify(res.tempFilePaths));
					success:res=>{
						// console.log(res)
						this.ImgArr = res.tempFilePaths
					}
					})
				},
			previewImg(current){
				console.log(current)
				uni.previewImage({
					current,
					urls : this.ImgArr,
					loop:true,
					indicator:'number'
						});
			}
			}
		}
</script>

<style>

</style>
