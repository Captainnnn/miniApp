<template>
	<view>
		
																																											<!-- 后面换成id -->
		<view class="meetingRoomItem" v-for="item in meetingRoomList" :key="item.imgSrc" :data-meetingRoomId="item.imgSrc" @click="meetingRoomDetail($event)">
			
			
			<view class="roomInfo">
				
				<image class="roomImg" :src="item.imgSrc"></image>
				
				
				<view class="baseInfo">
					<text class="title">{{item.title}}</text>
					
					<text class="maxPerson">坐席{{item.maxPerson}}人</text>
					
					<view class="feature">
						
						<view class="featureItem" v-for="fe in item.feature" :key="fe">
							{{fe}}
						</view>
						
						
					</view>
					
					<text class="needScore">所需积分：{{item.needScore}}/0.5h</text>
					
				</view>
				
				
			</view>
			
			<text class="address">会议室地点：{{item.address}}</text>
			
			<hr>
			
			<text class="roomDetail">点击查看详情>></text>
			
			
			
			
		</view>
		
		
		
		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				meetingRoomList:[]
			};
		},
		methods:{
			meetingRoomDetail(event){
				uni.navigateTo({
					url:"meetingRoomDetailPage/meetingRoomDetailPage?id=" + event.currentTarget.dataset.meetingroomid
				})
			}
		},
		created() {
			uni.request({
				url:"https://mock.yonyoucloud.com/mock/11982/meetingRoom",
				success: (res) => {
					this.meetingRoomList = res.data.data;
					console.log(this.meetingRoomList);
				}
			})
		}
	}
</script>

<style lang="scss">
	.meetingRoomItem{
		display: flex;
		flex-direction: column;
		margin: 20rpx;
		border: 1rpx solid #9f9f9f;
		border-radius: 20rpx;
		box-shadow: 0rpx 2rpx 10rpx 0rpx;
	}
	.roomInfo{
		display: flex;
	}
	.roomImg{
		width: 230rpx;
		height: 230rpx;
		margin: 10rpx 20rpx;
	}
	.baseInfo{
		
	}
	.title{
		display: block;
		font-weight: 700;
		text-align: center;
	}
	.maxPerson{
		display: block;
		font-size: 30rpx;
	}
	.feature{
		display: flex;
		margin-top: 15rpx;
	}
	.featureItem{
		border: 1rpx solid #a7a7a7;
		border-radius: 10rpx;
		font-size: 25rpx;
		margin: 5rpx;
		padding: 5rpx;
	}
	.needScore{
		display: block;
		color: #fd8813;
		margin-top: 20rpx;
	}
	.address{
		color: #b1b1b1;
		font-size: 26rpx;
	}
	.roomDetail{
		text-align: center;
		font-size: 30rpx;
		color: #7c7c7c;
		margin: 10rpx;
	}

</style>
