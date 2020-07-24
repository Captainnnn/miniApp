<template>
	<view>
		

		
		<uni-segmented-control :current="current" :values="items" @clickItem="onClickItem" style-type="text" active-color="#ffab03"></uni-segmented-control>
		
		
		
		<view class="content">
			<view v-if="current === 0">
				<government-subsidy></government-subsidy>
			</view>
			<view v-if="current === 1">
				<industry-policy></industry-policy>
			</view>
			<view v-if="current === 2">
				<government-files></government-files>
			</view>
		</view>
		
		
		
		
		
		
	</view>
</template>

<script>
	import uniSegmentedControl from "../../../components/uni-segmented-control/uni-segmented-control.vue"
	import governmentSubsidy from "../../../components/governmentSubsidy/governmentSubsidy.vue"
	import industryPolicy from "../../../components/industryPolicy/industryPolicy.vue"
	import governmentFiles from "../../../components/governmentFiles/governmentFiles.vue"
	
	export default {
		data() {
			return {
				items: ['政府补贴', '产业政策', '政府文件'],
				current: 0
			}
		},
		methods: {
			onClickItem(e) {
				if (this.current !== e.currentIndex) {
					this.current = e.currentIndex;
				}
			}
		},
		components: {
			uniSegmentedControl,
			governmentSubsidy,
			industryPolicy,
			governmentFiles
		}
	}
</script>

<style>

</style>
