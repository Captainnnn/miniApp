<template>
	<view>
		
		
		
		<meeting-room-detail :meetingRoomId="meetingRoomId"></meeting-room-detail>
		
		
		
		
		
		
	</view>
</template>

<script>
	import meetingRoomDetail from '../../../../components/meetingRoomDetail/meetingRoomDetail.vue'
	
	export default {
		data() {
			return {
				meetingRoomId:null,
			}
		},
		onLoad(rec) {
			// console.log(rec);
			this.meetingRoomId = rec.id;
		},
		methods: {
			
		},
		components:{
			meetingRoomDetail
		}
	}
</script>

<style>

</style>
