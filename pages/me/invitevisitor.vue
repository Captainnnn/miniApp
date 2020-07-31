<template>
	<view>
		<view class="box">
			<view class="box_left" v-bind:class="[one?activeClass:'']" @click="myworkstation">我的会议室</view>
			<view class="box_right" v-bind:class="[two?activeClass:'']" @click="histroy">历史记录</view>
		</view>
		<view class="line"></view>
		<swiper :indicator-dots="indicatorDots"  :interval="interval" :duration="duration" class="swiper"
		:current="current" @change="change">
			<swiper-item>
				<scroll-view scroll-y="true" @scrolltolower="lower" style="height: 100%;">
					<block v-for="(item_one, index) in 10">
						<view class="container" @click="godeatil">
							<view class="container_left"></view>
							<view class="container_right">
								<view class="text">文化礼堂</view>
								<view style="margin-left:30rpx;font-size:28rpx;">地点：数学与信息学院二楼</view>
								<view class="time">时间：6月21日 15：00 - 16：00</view>
							</view>
						</view>
					</block>
				</scroll-view>
			</swiper-item>
			<swiper-item>
				<scroll-view scroll-y="true" @scrolltolower="lower" style="height: 100%;">
					<block v-for="(item_one, index) in 10">
						<view class="tank">
							<view class="center">张三</view>
							<view class="center">19927532750</view>
							<view class="center">腾讯</view>
						</view>
					</block>
				</scroll-view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				one:true,
				two:false,
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500,
				current:0,
				activeClass:"green"
			}
		},
		methods: {
			change:function(e){
				console.log(e); //e.detail.current 就是改变之后的额那个页面的索引
				this.$data.current=e.detail.current
				if(e.detail.current==0){
					this.setone()
				}else{
					this.settwo()
				}
			},
			lower:function(e){
				uni.showToast({
				    title: '没有更多了',
				    duration: 2000
				});
			},
			godeatil:function(){
				uni.navigateTo({
				    url: 'visitordetail',
				    animationType: 'pop-in',
				    animationDuration: 200
				});
			},
			myworkstation:function(e){
				this.$data.current=0;
				this.setone()
				
			},
			histroy:function(e){
				this.$data.current=1;
				this.settwo()
			},
			setone:function(e){
				this.$data.one=true;
				this.$data.two=false;
			},
			settwo:function(e){
				this.$data.one=false;
				this.$data.two=true;
			}
		}
	}
</script>

<style>
	.box{
		height: 100rpx;
		width: 100vw;
		display: flex;
	}
	.box_left{
		height: 100rpx;
		line-height: 100rpx;
		width: 50vw;
		text-align: center;
	}
	.box_right{
		height: 100rpx;
		line-height: 100rpx;
		width: 50vw;
		text-align: center;
	}
	.line{
		background-color: #C0C0C0;
		height: 10rpx;
		width: 100vw;
	}
	.green{
		color: #4CD964;
	}
	.container{
		height:200rpx;
		width: 95vw;
		background-color: #C0C0C0;
		margin: 20rpx auto;
		border-radius: 10rpx;
	}
	.container_left{
		height: 150rpx;
		width: 30vw;
		float: left;
		background-color: #1CBBB4;
		position: relative;
		left: 10rpx;
		top:25rpx;
	}
	.container_right{
		float: right;
		width: 65vw;
	}
	.time{
		font-size: 28rpx;
		margin-left:30rpx;
		margin-top: 10rpx;
	}
	.text{
		margin-top:25rpx;
		margin-left: 30rpx;
		margin-bottom: 10rpx;
		font-weight: 800;
	}
	.swiper{
		height: 92vh;
	}
	.tank{
		display: flex;
		height: 100rpx;
		width: 95vw;
		margin: 15rpx auto;
		justify-content:space-around;
		background-color: #C0C0C0;
		border-radius: 10rpx;
	}
	.center{
		line-height: 100rpx;
	}
</style>
