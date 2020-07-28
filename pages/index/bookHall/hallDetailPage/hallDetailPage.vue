<template>
	<view>
		
		
		<hall-detail :hallId="detailId"></hall-detail>
		
		
		
		
	</view>
</template>

<script>
	import hallDetail from "../../../../components/hallDetail/hallDetail.vue"
	
	export default {
		data() {
			return {
				detailId:null
			}
		},
		methods: {
			
		},
		onLoad(rec) {
			this.detailId = rec.id;
			// console.log(rec.id);
		},
		created: () => {
		},
		components:{
			hallDetail
		}
	}
</script>

<style>

</style>
