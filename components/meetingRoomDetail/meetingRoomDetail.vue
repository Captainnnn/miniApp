<template>
	<view class="container">

		<text class="title">
			{{meetingRoomInfo.title}}
		</text>

		<image class="meetingRoomImg" :src="meetingRoomInfo.imgSrc"></image>

		<view class="personAndScore">

			<text class="maxPerson">座位数：{{meetingRoomInfo.maxPerson}}</text>

			<text class="score">{{meetingRoomInfo.needScore}}积分/0.5h</text>

		</view>

		<text class="address">地址：{{meetingRoomInfo.address}}</text>

		<view class="feature">

			<view class="featureItem" v-for="fe in meetingRoomInfo.feature" :key="fe">
				{{fe}}
			</view>

		</view>

		<view class="article">
			会议主题：<input class="inputArticle" type="text" placeholder="主题" />
		</view>

		<view class="describe">
			会议描述：<textarea type="text" placeholder="描述" />
			</view>
		
		<view class="selectDate">
		
			选择日期：
			<picker mode="date" :value="date" @change="bindDateChange">{{date}}</picker>
		
		</view>
		
		<view class="speaker">
			主持人：<input type="text" placeholder="主持人" />
		</view>
		
		<button class="advance" plain="true">立即预定</button>
		
		
		
	</view>
</template>

<script>
	import DateTimePicker from '../bory-dateTimePicker/bory-dateTimePicker.vue'
	
	export default {
		data() {
			return {
				meetingRoomInfo:{},
				date: this.getDate()
			};
		},
		props:{
			meetingRoomId:{
				type:String,
				default:""
			}
		},
		created() {
			console.log(this.meetingRoomId);
			uni.request({
				url:"https://mock.yonyoucloud.com/mock/11982/meetingRoomDetail?id=" + this.meetingRoomId,
				success: (res) => {
					this.meetingRoomInfo = res.data.data;
					console.log(this.meetingRoomInfo);
				}
			})
		},
		methods:{
			bindDateChange: function(e) {
				this.date = e.target.value;
			},
			getDate(type) {
				const date = new Date();
				let year = date.getFullYear();
				let month = date.getMonth() + 1;
				let day = date.getDate();
			
				if (type === 'start') {
					year = year - 60;
				} else if (type === 'end') {
					year = year + 2;
				}
				month = month > 9 ? month : '0' + month;;
				day = day > 9 ? day : '0' + day;
				return `${year}-${month}-${day}`;
			}
		},
		components:{
			DateTimePicker
		}
	}
</script>

<style>
	.container{
		display: flex;
		flex-direction: column;
	}
	.title{
		display: block;
		text-align: center;
		font-weight: 700;
		font-size: 40rpx;
	}
	.meetingRoomImg{
		width: 80%;
		height: 300rpx;
		margin: 0 auto;
		border: 1rpx solid red;
		border-radius: 20rpx;
	}
	.personAndScore{
		width: 80%;
		display: flex;
		margin: 20rpx auto;
	}
	.maxPerson{
		margin: 0rpx 40rpx;
	}
	.score{
		color: #fd8813;
		margin-left: 20rpx;
	}
	.address{
		color: #919191;
		font-size: 30rpx;
		text-align: center;
	}
	.feature{
		display: flex;
		justify-content: space-around;
		width: 80%;
		margin: 5rpx auto;
	}
	.featureItem{
		border: 1rpx solid #8b8b8b;
		border-radius: 10rpx;
		font-size: 30rpx;
		margin: 5rpx;
		padding: 5rpx 15rpx;
	}
	.article{
		font-weight: 700;
		margin: 0 auto;
		
	}
	.inputArticle{
		font-weight: 400;
		display: inline-block;
		border: 1rpx solid #000000;
	}
	.describe{
	margin: 10rpx auto;
	}
	textarea{
		border: 1rpx solid #000000;
	}
	.selectDate{
		margin: 10rpx auto;
	}
	picker{
		display: inline-block;
		border: 1rpx solid #000000;
	}
	.speaker{
		margin: 10rpx auto;
	}
	.speaker input{
		display: inline-block;
		border: 1rpx solid #000000;
	}
	.advance {
		background-color: #ff6201;
		position: fixed;
		/* width: 300rpx; */
		height: 80rpx;
		line-height: 80rpx;
		font-size: 40rpx;
		right: 0;
		bottom: 0;
	}
</style>
