<template>

	<view>
		<uni-segmented-control :current="current" :values="items" @clickItem="onClickItem" style-type="text" active-color="#ffab03"></uni-segmented-control>
		<view class="content">
			<view v-if="current === 0">
				<company-service-secretary></company-service-secretary>
			</view>
			<view v-if="current === 1">
				<company-service-account></company-service-account>
			</view>
			<view v-if="current === 2">
				<company-service-knowledge></company-service-knowledge>
			</view>
			<view v-if="current === 3">
				<company-service-human></company-service-human>
			</view>
			<view v-if="current === 4">
				<company-service-hire></company-service-hire>
			</view>
		</view>
	</view>

</template>

<script>
	import uniSegmentedControl from "../../../components/uni-segmented-control/uni-segmented-control.vue"

	import companyServiceSecretary from "../../../components/companyServiceSecretary/companyServiceSecretary.vue"
	import companyServiceAccount from "../../../components/companyServiceAccount/companyServiceAccount.vue"
	import companyServiceKnowledge from "../../../components/companyServiceKnowledge/companyServiceKnowledge.vue"
	import companyServiceHuman from "../../../components/companyServiceHuman/companyServiceHuman.vue"
	import companyServiceHire from "../../../components/companyServiceHire/companyServiceHire.vue"

	export default {
		data() {
			return {
				items: ['秘书服务', '财务审计', '知识产权', '人力外包', '设备租赁'],
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
		beforeCreate() {
			console.log("before companyService created");
		},
		created() {
			console.log("companyService created!");
		},
		components: {
			uniSegmentedControl,
			companyServiceSecretary,
			companyServiceAccount,
			companyServiceKnowledge,
			companyServiceHuman,
			companyServiceHire
		}
	}
</script>

<style>

</style>
