<template>
	<view>
		<scroll-view scroll-y="true" @scrolltolower="lower" >
			<uni-rate pituresrc="../../static/message/business.png" ></uni-rate>
			<uni-rate pituresrc="../../static/message/coupon.png" ></uni-rate>
			<uni-rate pituresrc="../../static/message/pioneer.png" ></uni-rate>
			<uni-rate pituresrc="../../static/message/othermessage.png" ></uni-rate>
			<uni-rate pituresrc="../../static/message/business.png" ></uni-rate>
		</scroll-view>
	</view>
</template>

<script>
	import uniRate from '@/components/messageCom.vue'
	export default {
		components:{
			uniRate
		},
		data() {
			return {
				pituresrc:"../../static/message/pioneer.png",
				type:"创业活动",
				time:"06-22 12:00 2020",
				content:"阿里云服务器把必胜客纳斯达克祭敖包山东矿机八边形节哀顺变的骄傲网贷巴士，啊什么呢大，是九点半，插拔式擦按时吃"
			}
		},
		methods:{
			lower:function(e){
				console.log(e)
				uni.showToast({
				    title: '没有更多了',
				    duration: 2000
				});
			}
		}
	}
</script>

<style>
	page{
		height: 100%;
		width: 100%;
		background-color: #F3EDED;
	}
	.container{
		display: flex;
		width:88vw;
		margin: 30rpx auto;
		background-color: #FFFFFF;
		border-radius: 30rpx;
	}
	.piturebox{
		width:100rpx;
		height:250rpx;
		margin: 10rpx auto;
	}
	.right{
		width: 70vw;
		height: 250rpx;
		position: relative;
		padding-top: 8rpx;
	}

	.piture{
		height: 100rpx;
		width: 100rpx;
	}
	.top{
		height: 50rpx;
	}
	.bottom{
		height: 200rpx;
		margin-top: 4rpx;
	}

</style>
