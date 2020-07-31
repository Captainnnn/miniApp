<template name="coupan">
	<view class="bg">
		<QSCoupon>
			<!-- 需要定义宽高，比例最好与遮罩图片相等 -->
			<view class="flex_row coupon"
			:style="{
				'background-color': backgroundColor,
				'color': color
			}">
			<!-- 根据内部比例设置flex属性 -->
				<view class="padding_15rpx flex_column_between_none fontSize_23rpx" style="flex: 519;">
					<view class="">
						{{shopuse}}
					</view>
					<view class="fontSize_33rpx">
						￥：{{value}}   {{cardType}}
					</view>
					<view class="">
						有效期至 {{effectiveDate}}
					</view>
					<view class="">
						券号: {{cardId}}
					</view>
					<view class="">
						{{content}}
					</view>
				</view>
				<view class="flex_row_c_c fontSize_21rpx" style="flex: 182;" @click="use">
					{{useType}}
				</view>
			</view>
		</QSCoupon>
	</view>
</template>

<script>
	import QSCoupon from './QS-coupon.vue';
	export default {
		components: {
			QSCoupon
		},
		name:"coupon",
		props:{
			cardType:{
				type:String,
				default:"现金券"
			},
			effectiveDate:{
				type:String,
				default:"2020.07.24"
			},
			cardId:{
				type:String,
				default:"1213546"
			},
			content:{
				type:String,
				default:"满200元减90元"
			},
			value:{
				type:String,
				default:"90"
			},
			shopuse:{
				type:String,
				default:"碧水花园"
			},
			backgroundColor:{
				type:String,
				default:"#f1505c"
			},
			color:{
				type:String,
				default:"white"
			},
			useType:{
				type:String,
				default:"立即使用"
			}
		},
		data() {
			return {
				list: [
					{
						backgroundColor: '#f1505c',
						color: 'white'
					},
					{
						backgroundColor: '#3d3b4f',
						color: '#ca6924'
					},
					{
						backgroundColor: '#f3f9f1',
						color: '#ffc64b'
					},
					{
						backgroundColor: '#4c8dae',
						color: 'white'
					},
					{
						backgroundColor: '#3d3b4f',
						color: 'white'
					},
					{
						backgroundColor: '#d6ecf0',
						color: '#ff8c31'
					},
					{
						backgroundColor: '#bacac6',
						color: '#eedeb0'
					}
				]
			}
		},
		mounted() {
			console.log(this);
			console.log(this.useType)
		},
		methods: {
			use:function(e){
				console.log("点击立即使用")
			}
		}
	}
</script>

<style >
	.bg{
		background: url("http://imgsrc.baidu.com/forum/w%3D580/sign=f992cfd546fbfbeddc59367748f1f78e/6c7667d0f703918f03d163205c3d269758eec4ad.jpg");
		background-repeat: repeat-y;
		background-size: contain;
		background-origin: border-box;
		background-size: 100vw 100vh;
	}
	.coupon{
		width: 600rpx;
		height: 234rpx;
	}
	.marginTop_45rpx {
		margin-top: 45rpx;
	}
	.null_20rpx{
		height: 20rpx;
	}
	.fontSize_21rpx {
		font-size: 21rpx;
	}
	.fontSize_33rpx {
		font-size: 33rpx;
	}
	.fontSize_23rpx {
		font-size: 23rpx;
	}
	.flex_column_between_none {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
	.padding_15rpx {
		padding: 15rpx;
	}
	.flex_row {
		display: flex;
		flex-direction: row;
	}
	.flex_row_c_c {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}
	.flex_column {
		display: flex;
		flex-direction: column;
	}
	.width100 {
		width: 100%;
	}
</style>
