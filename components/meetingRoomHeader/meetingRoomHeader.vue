<template>
	<view>
		<view class="header">

			<uni-combox label="" :candidates="candidates" placeholder="输入城市" v-model="city"></uni-combox>

			<view class="selectDate">

				选择日期：
				<picker mode="date" :value="date" @change="bindDateChange">{{date}}</picker>

			</view>


		</view>

	</view>
</template>

<script>
	import uniCombox from "../uni-combox/uni-combox.vue"
	import DateTimePicker from '../bory-dateTimePicker/bory-dateTimePicker.vue'

	export default {
		data() {
			return {
				candidates: ["广州", "惠州"],
				city: "",
				date: this.getDate()
			};
		},
		methods: {
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
		components: {
			uniCombox,
			DateTimePicker
		}
	}
</script>

<style>
	.header {
		display: flex;
	}
	.selectDate{
		display: flex;
		flex: 1;
		font-size: 30rpx;
		color: #939393;
		align-items: center;
		height: 40rpx;
		border: 1rpx solid #909090;
		border-radius: 10rpx;
		margin: 10rpx 5rpx;
		padding: 5rpx;
	}
</style>
