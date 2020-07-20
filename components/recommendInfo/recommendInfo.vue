<template>
		<view class="recommend-comtainer">
			
			<view class="recommend" v-for="item in recommendInfo">
				<text class="recommend-text">
					|{{item.name}}
				</text>
				<image class="recommend-icon" :src="item.path" lazy-load="true"></image>
			</view>
			
		</view>
</template>

<script>
	export default {
		data() {
			return {
				recommendInfo:[]
			};
		},
		created() {
			uni.request({
				url:"https://mock.yonyoucloud.com/mock/11982/getRecommend",
				success: (res) => {
					this.recommendInfo = res.data.data;
					console.log(this.recommendInfo);
				}
			})
		}
	}
</script>

<style>
	/* *{
		margin: 0;
		padding: 0;
	} */
	.recommend{
		/* width: 351rpx; */
		/* height: 190rpx; */
		margin: 25rpx 30rpx;
	}
	.recommend-text{
		/* display: block; */
		font-size: 25rpx;
		/* padding-left: 30rpx; */
		margin-bottom: 10rpx;
	}
	.recommend-icon{
		display: block;
		width: 100%;
		height: 330rpx;
		margin: 0 auto;
		border: 2rpx solid black;
	}

</style>
