<template>
	<view style="position: relative;">
		<!-- 条目 -->
		<scroll-view scroll-y="true" style="height: 900rpx;">
			<block v-for="(item_one, index) in 10">
				<view class="tank" >
					<view class="center">张三</view>
					<view class="center">19927532750</view>
					<view class="center">腾讯</view>
					<view class="remove" @click="remove">移除</view>
				</view>
			</block>
		</scroll-view>
		<!-- 表单位置 -->
		<form @submit="confirm"  class="form" v-if="two">
			<view class="uni-form-item uni-column">
			    <view class="title">被邀请人姓名</view>
				<input class="uni-input" focus placeholder="姓名" name="name" />
			</view>
			<view class="uni-form-item uni-column">
			    <view class="title">被邀请人手机号</view>
				<input class="uni-input" focus  placeholder="手机号" name="telephone"/>
			</view>
			<view class="uni-form-item uni-column">
			    <view class="title">被邀请人所属公司</view>
				<input class="uni-input" focus placeholder="公司" name="company"/>
			</view>
			<view class="form_box">
				<button size="mini" type="default" @click="cancel" >取消</button>
				<button size="mini" type="primary" form-type="submit" >确认</button>
			</view>
			
		</form>
		<!-- 添加按键 -->
		<button  @click="addUser">添加</button>
		<!-- 灰色挡板，蒙版 -->
		<view class="mask" v-if="two"></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				one:true,
				two:false,       //需不需要蒙版，    
			}
		},
		methods: {
			addUser:function(e){
				console.log("添加");
				this.$data.two=true;
			},
			remove:function(e){
				//移除逻辑
			},
			confirm:function(e){
				console.log(e)   //e.detail.value.company 公司 ，类推
				//获取表单数据
				
				//对表单的数据进行过滤和检验
				
				//调用接口，向服务器提交表单
				
				//成功之后设置设置蒙版消失,同时隐匿自己。
				this.$data.two=false;
				
			},
			cancel:function(){
				//点击取消之后取消蒙版
				this.$data.two=false;
			}
		}
	}
</script>

<style>
	.tank{
		display: flex;
		height: 100rpx;
		width: 95vw;
		margin: 15rpx auto;
		justify-content:space-around;
		background-color: #C0C0C0;
		border-radius: 10rpx;
		z-index: 1;
		position: relative;
	}
	.center{
		line-height: 100rpx;
	}
	.remove{
		background-color: #ED1C24;
		height:50rpx;
		width: 90rpx;
		margin: auto 0;
		text-align: center;
		line-height: 50rpx;
		border-radius: 13rpx;
	}
	.shelter{
		position: relative;
		z-index: -2;
		height: 200rpx;
		width: 100vw;
		background-color:#FFFFFF;
		opacity: 0.1;
	
	}
	.mask{
		 width: 100%;
		 height: 100%;
		 position: fixed;
		 top: 0;
		 left: 0;
		 background: #000;
		 z-index: 9;
		 opacity: 0.7;
	}
	page{
		z-index: 3;
		position: relative;
	}
	.title {
	    padding: 10rpx 0;
	}
	.uni-form-item{
		width: 92vw;
		margin: 35rpx auto;
	}
	.uni-input-wrapper {
        /* #ifndef APP-NVUE */
        display: flex;
        /* #endif */
        padding: 8px 13px;
        flex-direction: row;
        flex-wrap: nowrap;
        background-color: #FFFFFF;
    }
	.uni-input {
        height: 28px;
        line-height: 28px;
        font-size: 15px;
        padding: 0px;
        flex: 1;
        background-color: #FFFFFF;
		width: 92vw;
		border-radius: 10rpx;
		box-shadow: 5px 5px 5px #888888;
    }
	.uni-form-item__title {
        font-size: 16px;
        line-height: 24px;
    }
	.form{
		position: fixed;
		height: 566rpx;
	    width: 100vw;
		background-color:#DDDDDD;
		top: 300rpx;
		z-index: 9999;
	}
	.form_box{
		display: flex;
		width: 100vw;
		 justify-content:space-around
	}
	.cancel{
		border-radius: 5rpx ;
		float: right;
		position: relative;
		right: 50rpx;
		top: 5rpx;
	}
	.confirm{
		border-radius: 5rpx ;
		float: right;
		position: relative;
		right: 20rpx;
		top: 5rpx;
	}
</style>
