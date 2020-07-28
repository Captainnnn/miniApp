<template>
	<view class="policy-container">


		<view class="policyItem" v-for="item in governmentSubsidyList" :key="item.id" v-if="item.type === 1">


			<view class="policyTitle">
				{{item.title}}
			</view>


			<!-- <view class="policyDetail"> -->

			<!-- <text class="policyText">1</text> -->

			<image class="policyImg" :src="item.imgSrc"></image>



			<!-- </view> -->

		</view>



	</view>
</template>

<script>
	export default {
		data() {
			return {
				governmentSubsidyList: []
			};
		},
		created() {
			uni.request({
				url: "https://mock.yonyoucloud.com/mock/11982/policy",
				success: (res) => {
					this.governmentSubsidyList = res.data.data;
					console.log(this.governmentSubsidyList);
				}
			})
		}
	}
</script>

<style>
	.policyItem {
		display: flex;
		margin: 15rpx;
		padding: 15rpx;
		border-radius: 25rpx;
		box-shadow: 0 3rpx 20rpx 2rpx rgba(177, 177, 177, 0.3);
	}

	.policyTitle {
		font-weight: 700;
		width: 70%;
	}

	.policyImg {
		width: 200rpx;
		height: 150rpx;
	}
</style>
