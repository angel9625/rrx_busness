<template>
	<view class="content">
		<view class="first-register" >
			<navigator url="./first_register" hover-class="none">
				<image :src="first"></image>
				<view class="text">首次申请</view>
			</navigator>
		</view>
		<view class="search-record">
			<navigator @click="pop_open" url="#" hover-class="none">
				<image :src="search"></image>
				<view class="text">申请查询记录</view>
			</navigator>
		</view>
		<uni-popup ref="popup" type="dialog">
				<uni-popup-dialog mode="input" title="申请查询记录" placeholder-class="pclass" placeholder="输入账号名/手机号"></uni-popup-dialog>
			</uni-popup>
		</view>			
</template>

<script>
	import search from "../../static/images/register/search-record.png"
	import first from "../../static/images/register/first-register.png"
	// 导入uni弹出层组件
	import uniPopup from '@/components/uni-popup/uni-popup.vue'
	import uniPopupMessage from '@/components/uni-popup/uni-popup-message.vue'
	import uniPopupDialog from '@/components/uni-popup/uni-popup-dialog.vue'
	
	export default{
		components: {
		        uniPopup,
		        uniPopupMessage,
		        uniPopupDialog
		    },
		data(){
			return{
				first:first,
				search:search
			}
		},
		methods:{
			pop_open(){
				this.$refs.popup.open()
			}
		}
	}
</script>

<style lang="less" scoped>
	// 共用属性
	@conmon:{
		padding-top: 40rpx;
		height: 320rpx;
		background-color: rgb(242,242,242);
	}
	.content{
		text-align: center;
		image{
			width: 140rpx;
			height: 140rpx;
			padding-bottom: 30rpx;
		}
		.first-register{
			margin: 70rpx 0;
			@conmon();
		}
		.search-record{
		@conmon();
		}
		.text{
			font-size: 32rpx;
		}
	}
	.pclass{
		padding-left: 10rpx;
	}
</style>
