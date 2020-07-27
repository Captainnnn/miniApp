<template>
	<view class="bgcolor">
		<hall-header></hall-header>
		<hall-list></hall-list>
		
		
		
	</view>
</template>

<script>
	import hallList from "../../../components/hallList/hallList.vue"
	import hallHeader from "../../../components/hallHeader/hallHeader.vue"
	
	export default {
		data() {
			return {
				
			}
		},
		created() {
			console.log("Hall created!");
			
			
		},
		methods: {
			
		},
		components:{
			hallList,
			hallHeader
		}
	}
</script>

<style>
	.bgcolor{
		background-color: #c2a69d;
	}

</style>
