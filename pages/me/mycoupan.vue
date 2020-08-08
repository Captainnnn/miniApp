<template>
	<view>
		<view class="box">
			<view class="box_left" v-bind:class="[one?'active':'']" @click="Unused">未使用</view>
			<view class="box_right" v-bind:class="[two?'active':'']" @click="Used">已使用</view>
			<view class="box_right" v-bind:class="[three?'active':'']" @click="Expired">已过期</view>
		</view>
		<view class="line"></view>
		<swiper :indicator-dots="indicatorDots"  :interval="interval" :duration="duration" class="swiper"
		:current="current" @change="change">
			<!-- 未使用 -->
			<swiper-item>
				<scroll-view scroll-y="true" style="height: 100%;">
					<view class="flex_column width100 bg">
						<!-- 循环数据 -->
						<view class="width100 flex_row_c_c marginTop_45rpx" v-for="(item, index) in list" :key="index">

							<coupon >
								
							</coupon>
						</view>

					</view>
				</scroll-view>
			</swiper-item>
			<!-- 已经使用 -->
			<swiper-item>
				<scroll-view scroll-y="true" style="height: 100%;">
					<view class="flex_column width100 bg">
						<!-- 循环数据 -->
						<view class="width100 flex_row_c_c marginTop_45rpx" v-for="(item, index) in list" :key="index">
			
							<coupon backgroundColor="#F2F2F2" color="#000000" useType="已使用">
								
							</coupon>
						</view>
			
					</view>
				</scroll-view>
			</swiper-item>
			<!-- 已经过期 -->
			<swiper-item>
				<scroll-view scroll-y="true" style="height: 100%;">
					<view class="flex_column width100 bg">
						<!-- 循环数据 -->
						<view class="width100 flex_row_c_c marginTop_45rpx" v-for="(item, index) in list" :key="index">
			
							<coupon backgroundColor="#F2F2F2" color="#000000" useType="已过期">
								
							</coupon>
						</view>
			
					</view>
				</scroll-view>
			</swiper-item>
			
		</swiper>
	</view>
</template>

<script>
	import coupon from '@/components/QS-coupon/coupan.vue';
	export default {
		components: {
			coupon
		},
		data() {
			return {
				one:true,
				two:false,
				three:false,
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500,
				current:0,
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
					}
				]
				
			}
		},
		methods: {
			change:function(e){
				console.log(e); //e.detail.current 就是改变之后的额那个页面的索引
				this.$data.current=e.detail.current
				if(e.detail.current==0){
					this.setone()
				}else if(e.detail.current==1){
					this.settwo()
				}else{
					this.setthree()
				}
			},
			//未使用
			Unused:function(e){
				this.setone()
				this.$data.current=0
			},
			//已使用
			Used:function(e){
				this.settwo()
				this.$data.current=1
			},
			//已过期
			Expired:function(e){
				this.setthree()
				this.$data.current=2
			},
			setone:function(){
				this.$data.one=true
				this.$data.two=false
				this.$data.three=false
			},
			settwo:function(){
				this.$data.one=false
				this.$data.two=true
				this.$data.three=false
			},
			setthree:function(){
				this.$data.one=false
				this.$data.two=false
				this.$data.three=true
			}
		}
	}
</script>

<style scoped>
	.swiper{
		height: 92vh;
	}
	.box{
		display: flex;
		height: 100rpx;
		line-height: 100rpx;
		justify-content: space-around;
		font-weight: 500;
	}
	.line{
		background-color: #C0C0C0;
		height: 10rpx;
		width: 100vw;
	}
	.active{
		color: #39B54A;
		animation-duration: 150ms;
	}
</style>
