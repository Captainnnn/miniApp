<template>
	<view>
		<form @submit="formSubmit" @reset="formReset">
			<textarea name="feedback" class="textarea"   placeholder-style="#aaaaaa" placeholder="请输入您宝贵的意见"/>
			<view class="uni-btn-v">
			    <button form-type="submit">Submit</button>
			    <button type="default" form-type="reset">Reset</button>
			</view>
		</form>
		
	
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			formSubmit:function(e){
				console.log(e); //e.detail.value  就是提交的的值，需要进行防止sql注入，过滤危险信息
			},
			formReset: function(e) {
			    console.log('清空数据')
			}
		}
	}
</script>

<style>
	.textarea{
		width: 90vw;
		height:50vh; 
		border-radius:20rpx;
		background-color:#EDE1D9;
		margin: 20rpx auto;
	}
</style>
