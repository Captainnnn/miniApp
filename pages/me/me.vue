<template>
	<view style="height: 100%;width: 100%;">
		<view class="back"></view>
		<view class="personCard">
			<view class="left"></view>
			<view class="right">
				<view class="personCard_top font"><text class="name">张三</text><text style="margin-left: 30rpx;">19927532750</text></view>
				<view class="personCard_middle font">腾讯 研发 前端</view>
				<view class="personCard_bottom font">广东省广州市天河区xxxxx</view>
			</view>
		</view>
		

		<view class="myorder">
			<view class="text">我的订单</view>
			<view class="myorder_bottom">
				<block v-for="(item,index) in list">
					<view class="gridone">
						<image :src="item.url" class="myorder_image"></image>
						<text class="myorder_text">{{item.text}}</text>
					</view>
				</block>
			</view>
		</view>
		
		<view class="container">
			<view class="funbottom" @click="mycoupan" v-bind:class="[one?activeClass:'']">
				<image src="../../static/message/coupon.png" class="funbottom_piture"></image>
				<view class="funbottom_text">我的优惠券</view>
				<image src="../../static/me/arrow.png" class="arrow"></image>
			</view>
			
			<view class="funbottom" @click="invite" v-bind:class="[two?activeClass:'']">
				<image src="../../static/me/inviteVisitor.png" class="funbottom_piture"></image>
				<view class="funbottom_text">访客邀请</view>
				<image src="../../static/me/arrow.png" class="arrow"></image>
			</view>
			
			<view class="funbottom" @click="feedback" v-bind:class="[three?activeClass:'']">
				<image src="../../static/me/opinion.png" class="funbottom_piture" ></image>
				<view class="funbottom_text">意见反馈</view>
				<image src="../../static/me/arrow.png" class="arrow"></image>
			</view>
		</view>
		
		
	</view>
</template>

<script>
	var self=this;
	export default {
		data() {
			return {
				one:false,
				two:false,
				three:false,
				activeClass:"chooseColor",
				list: [{
						url: '../../static/me/pay.png',
						text: '待付款',
					},{
						url: '../../static/me/received.png',
						text: '待收货',
					},{
						url: '../../static/me/comment.png',
						text: '待评价',
					},{
						url: '../../static/me/back.png',
						text: '退款/售后',
					},{
						url: '../../static/me/order.png',
						text: '全部订单',
					}]
			}
		},
		methods: {
			mycoupan:function(e){
				console.log(this.$data.one)
				this.$data.one=true;
				uni.navigateTo({
				    url: 'mycoupan',
				    animationType: 'pop-in',
				    animationDuration: 200
				});
				
			},
			invite:function(e){
				this.$data.two=true;
				uni.navigateTo({
				    url: 'invitevisitor',
				    animationType: 'pop-in',
				    animationDuration: 200
				});
			},
			feedback:function(e){
				this.$data.three=true;
				uni.navigateTo({
				    url: 'feedback',
				    animationType: 'pop-in',
				    animationDuration: 200
				});
			}
		},
		onShow:function(){
			this.$data.one=false;
			this.$data.two=false;
			this.$data.three=false;
		}
	}
</script>

<style>
	page{
		height: 100%;
		width: 100%;
		background-color: #F8F8F8;
	}
	.gridone{
		width: 19vw;
		height: 150rpx;
		border-radius: 10rpx;
		display: flex;
		flex-direction: column;
		justify-content:space-around;
		align-items:center
	}
	
	.back{
		height: 300rpx;
		width: 100vw;
		background-color: #59A0FF;
	}
	.personCard{
		height: 200rpx;
		width: 90vw;
		background-color: #CCCCCC;
		position: relative;
		left: 5vw;
		top: -150rpx;
		border-radius: 20rpx;
		display: flex;
	}
	.left{
		height: 140rpx;
		width: 140rpx;
		background-color: #4CD964;
		border-radius: 50%;
		position: relative;
		left: 20rpx;
		top: 20rpx;
	}
	.right{
		height: 100%;
		width: 70vw;
		margin-left:5vw;
	}
	.name{
		font-size: 40rpx;
		font-weight: 600;
	}
	.personCard_top{
		margin-top:20rpx ;
	}
	.personCard_middle{
		margin:7rpx 0;
	}
	.font{
		font-size: 30rpx;
		font-weight: 400;
	}
	.myorder{
		height: 190rpx;
		width: 95vw;
		background-color: #FFFFFF;
		border-radius: 20rpx;
		margin: -115rpx auto;
	}
	.myorder_bottom{
		display: flex;
		align-items:center;
		margin-top:20rpx auto;
		height: 150rpx;
		border-radius: 10rpx;
		width: 95vw;
	}
	.piture{
		height: 90rpx;
		width: 90rpx;
	}
	.fontsize{
		font-size: 20rpx;
		font-weight: 800;
		width: 90rpx;
		text-align: center;
	}
	.text{
		margin:5rpx 20rpx;
		font-size: 30rpx;
	}
	.funbottom{
		background-color: #FFFFFF;
		height: 100rpx;
		width: 95vw;
		margin: 20rpx 0;
		border-radius: 20rpx;
		margin-top: 20rpx;
		margin: 20rpx auto;
		
	}
	.funbottom_piture{
		float: left;
		height: 64rpx;
		width: 64rpx;
		position: relative;
		left: 40rpx;
		top: 19rpx;
	}
	.funbottom_text{
		float: left;
		height: 100rpx;
		line-height: 100rpx;
		font-size: 28rpx;
		position: relative;
		left: 70rpx;
	}
	.arrow{
		float:right;
		position: relative;
		height: 64rpx;
		width: 64rpx;
		right: 10rpx;
		top: 20rpx;
	}
	.container{
		position: relative;
		top: 136rpx;
	}
	.chooseColor{
		background-color:#EBEEF5;
	}
	.myorder_image{
		height: 50rpx;
		width: 50rpx;
	}
	.myorder_text{
		font-size: 26rpx;	
	}
</style>
