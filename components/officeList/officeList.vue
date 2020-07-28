<template>
	<view class="office-container">
																							<!-- 后面换成id这里用src进行测试 -->
		<view class="officeItem" v-for="item in officeList" :key="item.id" @click="toDetailPage(item.src)">

			<image :src="item.src" class="officeIcon"></image>

			<view class="officeInfo">
				<text class="officeTitleAndType">
					{{item.title}}|{{item.type}}
				</text>
				<text class="officeAddress">
					{{item.address}}
				</text>

				<view class="officePrice">
					{{item.price}}/h
				</view>

			</view>

		</view>




	</view>
</template>

<script>
	export default {
		data() {
			return {
				officeList: []
			};
		},
		methods:{
			toDetailPage(id){
				getApp().globalData.detailId = id;
				console.log(getApp().globalData.detailId);
				uni.navigateTo({
					url: "officeDetailPage/officeDetailPage"
				});
			}
		},
		globalData:{
			detailId:null
		},
		created() {
			uni.request({
				url: "https://mock.yonyoucloud.com/mock/11982/getOfficeList",
				success: (res) => {
					this.officeList = res.data.officeList;
					console.log(this.officeList);
				}
			})
		}
	}
</script>

<style>
	.officeItem {
		display: flex;
		/* justify-content: space-between; */
		margin: 30rpx;
		width: 680rpx;
		height: 200rpx;
		padding: 10rpx;
	}

	.officeIcon {
		height: 200rpx;
		width: 50%;
		border-radius: 20%;
		margin-right: 20rpx;
	}

	.officeInfo {}

	.officeTitleAndType {
		font-weight: 700;
		/* margin-top: 50rpx; */
	}

	.officeAddress {
		display: block;
		font-size: 15rpx;
		color: #919191;
		margin-top: 30rpx;
	}

	.officePrice {
		text-align: right;
	}
</style>
