<template>
	<view>


		<view class="listItem" v-for="item in accountList" :key="item.imgSrc" v-if="item.type===2">

			<image class="itemImg" :src="item.imgSrc"></image>

			<view class="itemDetail">

				<text class="itemTitle">
					{{item.title}}
				</text>

				<view class="priceAndBuy">

					<text class="money">￥{{item.price}}</text>

					<button type="primary" size="mini">购买服务</button>

				</view>

			</view>

		</view>



	</view>
</template>

<script>
	export default {
		data() {
			return {
				accountList: []
			};
		},
		beforeCreate() {
			console.log("before companyServiceAccount created");
		},
		created() {
			console.log("companyServiceAccount created!");
			uni.request({
				//后面改一下加参数获取不同类型
				url: "https://mock.yonyoucloud.com/mock/11982/serve",
				success: (res) => {
					this.accountList = res.data.data;
					console.log(this.accountList);
				}
			})
		}
	}
</script>

<style>
	.listItem {
		display: flex;

		margin: 20rpx;
		/* border: 1rpx solid black; */
		box-shadow: 0 5rpx 9rpx 2rpx rgba(0, 0, 255, .2);
	}

	.itemImg {
		width: 200rpx;
		height: 200rpx;
		margin: 20rpx;
		margin-right: 40rpx;
	}

	.itemDetail {
		margin: 20rpx;
	}

	.itemTitle {
		display: block;
		margin-bottom: 60rpx;
	}

	.priceAndBuy {
		width: 400rpx;
		height: 70rpx;
		display: flex;
		justify-content: space-between;
	}

	.money {
		font-size: 50rpx;
		font-weight: 700;
		color: #dd3c3c;
		margin-right: 30rpx;
	}
</style>
