<template>
	<view class="swiper-container">
		<view class="swiper">
			<swiper autoplay="true" circular="true">
				<swiper-item v-for="item in indexSwiper" :key="item.image_url">
					<image :src="item.image_url"></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="function">

			

			<view v-for="item in mainDetail" :key="item.id" class="main" :data-where="item.toWhere" @click="toTarget($event)">
				<image class="mainIcon" :class="item.class" :src="item.iconSrc"></image>
				<view class="mainText">{{item.content}}</view>
			</view>

			

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
				url: getApp().globalData.baseUrl + "home/banner",
				success: (res) => {
					// console.log(res);
					this.indexSwiper = res.data.data;
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
		height: 275rpx;
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
