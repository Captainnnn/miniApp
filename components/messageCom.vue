<template name="message">
	<view class="box">
		<view class="container">
			<view class="piturebox">
				<image :src="pituresrc"  class="piture"></image>
			</view>
			<view class="right">
				<view class="top">
					<text style="font-size: large;font-weight: 800;">{{actionType}}</text>
					<text style="float: right;position: absolute;right:16rpx;top:16rpx;font-size: 33rpx;
		font-weight: 200;">{{time}}</text>
				</view>
				<view class="bottom">
					{{content}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"message",
		props:{
			pituresrc:{
				type:String,
				default:"../static/message/pioneer.png"
			},
			actionType:{
				type:String,
				default:"活动类型"
			},
			time:{
				type:String,
				default:"06-22 12:00 2020"
			},
			content:{
				type:String,
				default:"阿里云服务器把必胜客纳斯达克祭敖包山东矿机八边形节哀顺变的骄傲网贷巴士，啊什么呢大，是九点半，插拔式擦按时吃"
			}
		},
		data() {
			return {
				//pituresrc:"../../static/message/pioneer.png",
				//actionType:"创业活动",
				//time:"06-22 12:00 2020",
				//content:"阿里云服务器把必胜客纳斯达克祭敖包山东矿机八边形节哀顺变的骄傲网贷巴士，啊什么呢大，是九点半，插拔式擦按时吃"
			}
		},
		methods:{
			
		}
	}
</script>

<style>
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
