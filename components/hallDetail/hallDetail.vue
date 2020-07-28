<template>
	<view class="container">

		<text class="hallTitle">

			{{hallInfo.title}}

		</text>

		<view class="scoreAndFeature">
			<view class="score">
				<uni-rate readonly="true" size="17" :value="hallInfo.score" color="#cccccc" active-color="#ff2c04"></uni-rate>

			</view>

			<view class="hallFeature">

				<view class="feature" v-for="fe in hallInfo.feature" :key="fe">{{fe}}</view>


			</view>

		</view>

		<hr>

		<swiper class="hallSwiper" autoplay="true" circular="rtue">
			<swiper-item v-for="item in hallInfo.imgList" :key="item">
				<image class="img" :src="item"></image>
			</swiper-item>

		</swiper>


		<text class="address">
			{{hallInfo.address}}
		</text>


		<view class="priceAndPerson">

			<text class="price">{{hallInfo.price - 200}} ~ {{hallInfo.price}}/h</text>

			<view class="person">
				<image class="personImg" src="../../static/office/maxPerson.png"></image>

				<text class="personNum">{{hallInfo.maxPerson - 15}} ~ {{hallInfo.maxPerson}}人</text>

			</view>

		</view>


		<text class="hallBusinessTime">
			营业时间：{{hallInfo.businessTime}}
		</text>


		<view class="phone">
			咨询电话：
			{{hallInfo.phoneNum}}

			<image class="phoneImg" src="../../static/office/phone.png"></image>

		</view>


		<button class="advance" plain="true">预约看路演厅</button>



	</view>
</template>

<script>
	import uniRate from "../uni-rate/uni-rate.vue"

	export default {
		data() {
			return {
				hallInfo: {}
			};
		},
		props: {
			hallId: {
				type: String,
				default: ""
			}
		},
		created() {
			console.log(this.hallId);
			uni.request({
				url: "https://mock.yonyoucloud.com/mock/11982/hallDetail?id=" + this.hallId,
				success: (res) => {
					this.hallInfo = res.data.data;
					console.log(this.hallInfo);
				}
			})
		},
		components: {
			uniRate
		}
	}
</script>

<style>
	.hallTitle {
		display: block;
		font-weight: 700;
		margin: 10rpx 0 20rpx 26rpx;
	}

	.scoreAndFeature {
		display: flex;
		margin-left: 26rpx;
		margin-bottom: 15rpx;
	}

	.score {
		/* margin-top: 20rpx; */
	}

	.hallFeature {
		display: flex;
		flex: 1;
	}

	.feature {
		
		font-size: 25rpx;
		border: 1rpx solid #919191;
		border-radius: 10rpx;
		margin-left: 30rpx;
		padding: 5rpx;
	}

	.hallSwiper {
		position: relative;
		/* display: block; */
		width: 80%;
		margin-top: 15rpx;
		left: 50%;
		transform: translate(-50%);
	}

	.img {
		width: 100%;
		margin: 0 10rpx;
	}

	.address {
		display: block;
		margin: 15rpx 26rpx;
		font-size: 25rpx;
		color: #646464;
	}

	.priceAndPerson {
		width: 100%;
		height: 60rpx;
		display: flex;
		font-size: 30rpx;
		margin: 15rpx 26rpx 0 26rpx;
	}

	.price {
		line-height: 60rpx;
	}

	.person {
		margin-left: 100rpx;
	}

	.personImg {
		width: 60rpx;
		height: 60rpx;
		vertical-align: middle;
	}

	.personNum {
		font-size: 26rpx;
		margin-left: 10rpx;
	}

	.hallBusinessTime {
		color: #55f470;
		font-size: 30rpx;
		margin-left: 26rpx;
	}

	.phone {
		font-size: 30rpx;
		margin: 15rpx 26rpx;
	}

	.phoneImg {
		width: 60rpx;
		height: 60rpx;
		vertical-align: middle;
		margin-left: 20rpx;
	}

	.advance {
		background-color: #ff6201;
		position: fixed;
		/* width: 300rpx; */
		height: 80rpx;
		line-height: 80rpx;
		font-size: 40rpx;
		right: 0;
		bottom: 0;
	}
</style>
