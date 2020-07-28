<template>
	<view>
		
		
		<view class="headerItem">
			
			
			<image class="headerImg" :src="headerBackGround"></image>
			
			<text class="headerText">路 演 厅</text>
			
			
		</view>
		
		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				headerBackGround:"https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2pwZy8xaFJlSGFxYWZhZFZ1OVd1d1FqdHJYRDI1ZkNKQTFLV01rNHVZa29ZVHRVT0JiZ1VSVHVNb0lLR1ljaWNwMkRGcElTVnJOazNiVDVBb1NnTFVacmhWd2cvNjQw?x-oss-process=image/format,png"
			};
		}
	}
</script>

<style>
	.headerItem{
		position: relative;
		width: 100%;
		height: 400rpx;
		/* margin-top: 20rpx; */
	}
	.headerImg{
		width: 100%;
		height: 100%;
	}
	.headerText{
		position: absolute;
		left: 13%;
		bottom: 45%;
		font-weight: 700;
		font-size: 80rpx;
		color: white;
		text-shadow: 10rpx 8rpx 10rpx #ff5e59;
	}

</style>
