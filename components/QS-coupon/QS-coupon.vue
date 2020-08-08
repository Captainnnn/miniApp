<!-- css mask 了解 https://blog.csdn.net/qq_44607694/article/details/90551133 -->
<template>
	<view class="QS-coupon-box">
		<view class="QS-coupon">
			<slot></slot>
		</view>
	</view>
</template>

<script>
</script>

<style scoped>
	.QS-coupon-box .QS-coupon{
		/* 遮罩图片 */
		mask: url(../../static/me/coupon_mask.png);
		mask-repeat: no-repeat;
		mask-composite: intersect;
		mask-size: contain;
	}
</style>
