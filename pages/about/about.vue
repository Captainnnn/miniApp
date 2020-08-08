<template>
	<view>
		<view class="piture">这是一张公司的标志介绍图片</view>
		<swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
			<swiper-item>
				<view class="swiper-item uni-bg-red">A</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item uni-bg-blue">B</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item uni-bg-green">C</view>
			</swiper-item>
		</swiper>
		<view class="middle">
			<view class="text" >公司简介</view>
			<scroll-view class="explanation" scroll-y="true">
				{{explanation}}
			</scroll-view>
		</view>
		<view class="bottom">
			<view class="text">招聘渠道</view>
			<view >
				<view class="text_two">1、简历投递至我们的专用邮箱:994892083@qq.com</view>
				<view class="text_two">2、访问我们的官网投递(www.baidu.com)</view>
				<view class="text_two">3、下载我们的app投递简历</view>
			</view>
		</view>
		<view class="final">
			<view class="text">联系方式</view>
			<view class="text_one">客服电话：1234-5678-987</view>
			<view class="text_one">官方网站：www.baidu.com</view>
			<view class="text_one">官方邮箱：abajbsaasddw@test.com</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500,
				explanation:"2015年11月3日晚，阿里巴巴集团与河北省人民政府在石家庄签署了“互联网+扶贫”合作备忘录。双方商定，将充分发挥阿里巴巴集团在互联网经济领域的立体化产业发展优势和影响力，在“互联网+扶贫”领域开展深入合作，实现优势互补、共同发展。"
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.piture{
		height:170rpx;
		width: 100vw;
		background-color:#3F536E;
	}
	.explanation{
		height: 400rpx;
		background-color: #C0C0C0;
	}
	.text{
		margin:10rpx 20rpx;
		font-size: 36rpx;
		font-weight: 600;
	}
	.text_one{
		margin:10rpx 20rpx;
		font-size: 33rpx;
		font-weight: 400;
	}
	.final{
		border-radius: 20rpx;
		width: 95vw;
		background-color: #DDDDDD;
		margin: 14rpx auto;
	}
	.text_two{
		margin-left: 20rpx;
		font-size: 26rpx;
		font-weight: 100;
	}
	.swiper{
		height: 300rpx;
		width: 100vw;
	}
	.swiper-item{
		height: 100%;
	}
	.uni-bg-red{
		background-color:#DD524D;
	}
	.uni-bg-blue{
		background-color:#007AFF;
	}
	.uni-bg-green{
		background-color: #4CD964;
	}
</style>
