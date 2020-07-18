<template>
	<view class="swiper-container">
		<view class="swiper">
			<swiper autoplay="true" circular="true">
				<swiper-item v-for="item in indexSwiper">
					<image :src="item.iconPath"></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="function">
			
			<view class="main" >
				<image class="mianIcon office-address" src="../../static/home/bookOffice.png"></image>
				<view class="text">办公选址</view>
			</view>
			<view class="main" >
				<image class="mianIcon book-meetingRoom" src="../../static/home/bookMeetingRoom.png"></image>
				<view class="text">订会议室</view>
			</view>
			<view class="main" >
				<image class="mianIcon book-hall" src="../../static/home/bookHall.png"></image>
				<view class="text">路演厅</view>
			</view>
			<view class="main" >
				<image class="mianIcon company-service" src="../../static/home/companyService.png"></image>
				<view class="text">企业服务</view>
			</view>
			<view class="main" >
				<image class="mianIcon policy-news" src="../../static/home/policyNews.png"></image>
				<view class="text">政策资讯</view>
			</view>
			<view class="main" >
				<image class="mianIcon scan-openDoor" src="../../static/home/scan.png"></image>
				<view class="text">扫码开门</view>
			</view>
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				indexSwiper: []
			};
		},
		created() {
			console.log("created!")
			uni.request({
				url: "https://mock.yonyoucloud.com/mock/11982/getSwiper",
				success: (res) => {
					this.indexSwiper = res.data.swiper;
					// console.log(this.indexSwiper);
				}
			})
		},
		mounted() {
			console.log("mounted!")
		}
	}
</script>

<style>
	swiper,
	image {
		width: 100%;
		height: 250rpx;
	}
	.swiper-container{
		position: relative;
		width: 100%;
		height: 390rpx;
	}
	.swiper{
		margin: 10rpx;
	}
	.function{
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		position: absolute;
		width: 63%;
		height: 250rpx;
		bottom: 1rpx;
		left: 50%;
		transform: translateX(-50%);
		background: rgba(207, 207, 207, 0.6);
		/* border-radius: 30rpx; */
		box-shadow: 0rpx 10rpx 15rpx 0rpx grey;
	}
	.main{
		width: 95rpx;
		height: 100rpx;
		/* background-color: red; */
		margin: 15rpx;
	}
	.mianIcon{
		width: 100%;
		height: 70%;
	}
	.text{
		font-size: 5rpx;
		text-align: center;
	}
</style>
