<template>
	<view class="swiper-container">
		<view class="swiper">
			<swiper autoplay="true" circular="true">
				<swiper-item v-for="item in indexSwiper" :key="item.iconPath">
					<image :src="item.iconPath"></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="function">

			<!-- <view class="main" @click="toTarget('bookOffice')">
				<image class="mainIcon office-address" src="../../static/home/bookOffice.png"></image>
				<view class="mainText">办公选址</view>
			</view> -->

			<view v-for="item in mainDetail" :key="item.id" class="main" :data-where="item.toWhere" @click="toTarget($event)">
				<image class="mainIcon" :class="item.class" :src="item.iconSrc"></image>
				<view class="mainText">{{item.content}}</view>
			</view>

			<!-- <view class="main" >
				<image class="mainIcon book-meetingRoom" src="../../static/home/bookMeetingRoom.png"></image>
				<view class="mainText">订会议室</view>
			</view>
			<view class="main" >
				<image class="mainIcon book-hall" src="../../static/home/bookHall.png"></image>
				<view class="mainText">路演厅</view>
			</view>
			<view class="main" >
				<image class="mainIcon company-service" src="../../static/home/companyService.png"></image>
				<view class="mainText">企业服务</view>
			</view>
			<view class="main" >
				<image class="mainIcon policy-news" src="../../static/home/policyNews.png"></image>
				<view class="mainText">政策资讯</view>
			</view>
			<view class="main" >
				<image class="mainIcon scan-openDoor" src="../../static/home/scan.png"></image>
				<view class="mainText">扫码开门</view>
			</view> -->

		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				mainDetail: [{
						class: "office-address",
						iconSrc: "../../static/home/bookOffice.png",
						content: "办公选址",
						toWhere: "bookOffice"
					},
					{
						class: "office-address",
						iconSrc: "../../static/home/bookMeetingRoom.png",
						content: "订会议室",
						toWhere: "bookMeetingRoom"
					},
					{
						class: "office-address",
						iconSrc: "../../static/home/bookHall.png",
						content: "路演厅",
						toWhere: "bookHall"
					},
					{
						class: "office-address",
						iconSrc: "../../static/home/companyService.png",
						content: "企业服务",
						toWhere: "companyService"
					},
					{
						class: "office-address",
						iconSrc: "../../static/home/policyNews.png",
						content: "政策资讯",
						toWhere: "policyNews"
					},
					{
						class: "office-address",
						iconSrc: "../../static/home/scan.png",
						content: "扫码开门",
						toWhere: "scanOpenDoor"
					},
				],
				indexSwiper: []
			};
		},
		methods: {
			toTarget(event) {
				// console.log(event.currentTarget.dataset.where);
				uni.navigateTo({
					url: event.currentTarget.dataset.where + "/" + event.currentTarget.dataset.where,
					success: (e) => {
						console.log(e);
					},
					fail: (e) => {
						console.log(e);
					}
				})
			}
		},
		created() {
			console.log("created!")
			uni.request({
				url: "https://mock.yonyoucloud.com/mock/11982/getSwiper",
				success: (res) => {
					this.indexSwiper = res.data.swiper;
					console.log(this.indexSwiper);
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

	.swiper-container {
		position: relative;
		width: 100%;
		height: 390rpx;
	}

	.swiper {
		margin: 10rpx;
	}

	.function {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		position: absolute;
		width: 63%;
		height: 250rpx;
		bottom: 1rpx;
		left: 50%;
		transform: translateX(-50%);
		background: rgba(207, 207, 207, 0.5);
		/* border-radius: 30rpx; */
		box-shadow: 0rpx 10rpx 15rpx 0rpx grey;
	}

	.main {
		width: 95rpx;
		height: 100rpx;
		/* background-color: red; */
		margin: 15rpx;
	}

	.mainIcon {
		width: 100%;
		height: 70%;
	}

	.mainText {
		font-size: 5rpx;
		font-weight: 700;
		text-align: center;
	}
</style>
