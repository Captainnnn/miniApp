<template>
	<view>
		
		
		<meeting-room-header></meeting-room-header>
		<meeting-room-list></meeting-room-list>
		
		
		
		
		
		
		
		
	</view>
</template>

<script>
	import meetingRoomList from "../../../components/meetingRoomList/meetingRoomList.vue"
	import meetingRoomHeader from "../../../components/meetingRoomHeader/meetingRoomHeader.vue"
	
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		},
		components:{
			meetingRoomList,
			meetingRoomHeader
		}
	}
</script>

<style>

</style>
