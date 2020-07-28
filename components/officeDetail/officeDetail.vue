<template>
	<view class="container">
	
	
		<swiper indicator-dots="true" autoplay="true" circular="true">
			<swiper-item v-for="img in officeInfo.imgList" :key="img">
				<image :src="img"></image>
			</swiper-item>
	
		</swiper>
	
	
		<text class="title">
			{{officeInfo.title}} | {{officeInfo.type}}
		</text>
	
	
		<view class="addressAndLocate">
			<text class="address">
				{{officeInfo.address}}
			</text>
	
			<image class="locate" src="../../static/office/locate.png"></image>
	
		</view>
	
	
	
		<view class="moneyAndPerson">
	
			<text class="price">{{officeInfo.price - 500}} ~ {{officeInfo.price}}/h</text>
	
			<view class="personNum">
	
				<image class="personImg" src="../../static/office/maxPerson.png"></image>
	
				<text class="person">
					{{officeInfo.maxPerson - 7}} ~ {{officeInfo.maxPerson}}人
				</text>
	
			</view>
	
		</view>
	
		<hr>
	
		<text class="message">
			简介：{{officeInfo.message}}
		</text>
	
		<hr>
	
	
		<view class="phone">
	
			<text class="phoneNum">
				咨询电话：{{officeInfo.phone}}
			</text>
			
			<image class="phoneImg" src="../../static/office/phone.png"></image>
			
			
		</view>
	
		<!-- <view class="bottonBar"> -->
		<button class="advance" plain="true">立即预约</button>
		<!-- </view> -->
	
	
	
	
	</view>
</template>

<script>
	export default {
		data() {
			return {
				officeInfo: {}
			}
		},
		methods: {
		
		},
		created() {
			// console.log(getApp().globalData.detailId);
			uni.request({
				url: "https://mock.yonyoucloud.com/mock/11982/officeDetail",
				success: (res) => {
					this.officeInfo = res.data.data;
					console.log(this.officeInfo);
				}
			})
		}
	}
</script>

<style>
	.container {
		/* position: relative; */
	}
	
	swiper,
	image {
		width: 100%;
		height: 300rpx;
		margin-top: 5rpx;
	}
	
	.title {
		display: block;
		font-weight: 700;
		margin: 20rpx 20rpx 5rpx 20rpx;
	}
	
	.address {
		font-size: 20rpx;
		color: #8e9091;
		margin-left: 20rpx;
	}
	
	.locate {
		width: 50rpx;
		height: 50rpx;
		vertical-align: middle;
		margin-left: 10rpx;
	}
	
	.moneyAndPerson {
		display: flex;
		height: 80rpx;
	}
	
	.price {
		font-size: 30rpx;
		margin-left: 10rpx;
		line-height: 80rpx;
	}
	
	.personNum {
		margin-left: 50rpx;
	}
	
	.personImg {
		width: 60rpx;
		height: 60rpx;
		margin: 5rpx;
		vertical-align: middle;
	}
	
	.person {
		font-size: 30rpx;
		line-height: 80rpx;
	}
	
	.message {
		display: block;
		margin: 30rpx;
		font-size: 25rpx;
		text-indent: 2em;
		line-height: 35rpx;
	}
	
	.phone{
		width: 100%;
		height: 70rpx;
		margin: 10rpx;
		margin-top: 20rpx;
	}
	.phoneNum{
		line-height: 70rpx;
	}
	.phoneImg{
		width: 60rpx;
		height: 60rpx;
		vertical-align: middle;
		margin: 0 0 0 15rpx;
	}
	
	.advance {
		background-color: #ff6201;
		position: fixed;
		width: 240rpx;
		height: 80rpx;
		line-height: 80rpx;
		font-size: 40rpx;
		right: 0;
		bottom: 0;
	}

</style>
