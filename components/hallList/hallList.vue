<template>
	<view class="background">
		
		
		
																																					<!-- 后面换成id -->
		<view class="hallItem" v-for="item in hallList" :key="item.name" :data-curId="item.id" @click="toHallDetail($event)">
			
			
			
			<view class="hallBody">
				
				<image class="hallImg" :src="item.image_url"></image>
				
				<view class="hallInfo">
					
					<view class="hallTitle">{{item.name}}</view>
					<view class="hallScore">
						<uni-rate readonly="true" size="17" :value="item.star" color="#cccccc" activeColor="#ff2c04"></uni-rate>
					<!-- {{item.score}} -->
					</view>
					
					<view class="hallFeature">
						
						<view class="feature" v-for="tag in item.tags" :key="tag">{{tag}}</view>
						
						
					</view>
					
					<view class="hallBusinessTime">{{item.free_time}}</view>
					
				</view>
				
				
				
			</view>
			
			
			<hr>
			
			<text class="readDetail">
				查看详情>
			</text>
			
			
			
		</view>
		
		
		
		
		
	</view>
</template>

<script>
	import uniRate from "../uni-rate/uni-rate.vue"
	
	export default {
		data() {
			return {
				hallList:[]
			};
		},
		methods:{
			toHallDetail(event){
				// console.log(event.currentTarget.dataset.curid);
				uni.navigateTo({
					url:"hallDetailPage/hallDetailPage?id=" + event.currentTarget.dataset.curid,
					success: () => {
						console.log("success!")
					},
					fail: (e) => {
						console.log(e)
					},
					complete: () => {
						console.log("complete!")
					}
				});
			}
		},
		created() {
			uni.request({
				url: getApp().globalData.baseUrl + "roadshow/brief?start=0&limit=10",
				success: (res) => {
					this.hallList = res.data.data;
					console.log(this.hallList);
				}
			})
		},
		components:{
			uniRate
		}
	}
</script>

<style>
	.background{
		padding: 10rpx;
	}
	
	.hallItem{
		width: 80%;
		background-color: #FFFFFF;
		margin: 30rpx auto;
		padding: 10rpx;
		/* border: 1rpx solid; */
		border-radius: 30rpx;
	}
	.hallBody{
		display: flex;
	}
	.readDetail{
		display: block;
		text-align: center;
		font-size: 25rpx;
		color: #646566;
	}
	.hallImg{
		width: 40%;
		height: 150rpx;
		margin: 10rpx;
	}
	.hallInfo{
		display: flex;
		flex-direction: column;
		margin-left: 10rpx;
	}
	.hallTitle{
		font-weight: 700;
		font-size: smaller;
		margin-bottom: 20rpx;
	}
	.hallScore{
		
	}
	.hallFeature{
		display: flex;
	}
	.feature{
		font-size: 15rpx;
		border: 1rpx solid #7e7e7e;
		color: #393939;
		border-radius: 8rpx;
		margin: 10rpx;
		padding: 3rpx;
	}
	.hallBusinessTime{
		font-size: 10rpx;
		padding: 5rpx;
	}

</style>
