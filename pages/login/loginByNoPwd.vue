<template>
	<view class="content">
		<view class="login-input">
			<image :src="phone"></image>
			<input v-model="username" maxlength="11" type="text" placeholder="账号/手机号" @blur="checkUsername"/>
		</view>
		<view class="login-input input-code">
			<image :src="pwd"></image>
			<input v-model="code" type="number" placeholder="请输入验证码" @blur="checkCode"/>
			<view class="code" v-show="isSend" @click="sendCode">发送验证码</view>
			<view v-show="!isSend" class="red">{{completetime}}</view>
		</view>
		<button class="login" @click="toLogin">登录</button>
	</view>
</template>

<script>
	import phone from "../../static/images/login/phone.png"
	import pwd from "../../static/images/login/pwd.png"
	
	export default{
		data(){
			return{
				phone:phone,
				pwd:pwd,
				username:"",
				code:"",
				isSend:true,
				completetime:0
			}
		},
		methods:{
			checkUsername(){
				if(!this.username){
					uni.showToast({
						title:"手机号不能为空",
						icon:"none"
					})
				}	
			},
			checkCode(){
				if(!this.code){
					uni.showToast({
						title:"验证码不能为空",
						icon:"none"
					})
				}				
			},
			// 发送验证码
			sendCode(){
				
			},
			// 登录
			toLogin(){
				if(!this.username || !this.code){
					uni.showToast({
						title:"手机号或验证码不能为空",
						icon:"none"
					})
				}
				else{
					uni.switchTab({
						url:"../order/order"
					})
				}
				
			}
		}
	}
</script>

<style lang="scss">
	.content{
		width: 90%;
		font-size: 30rpx;
		margin: 0 auto;
		padding-top: 80rpx;
		image{
			width: 28rpx;
			height: 33rpx;
			margin: auto 0;
		}
		.login-input{
			width: 95%;
			display: flex;
			border-bottom: 1rpx solid rgb(235,232,232);
			margin: 0 auto;
			input{
				padding: 30rpx;
			}
			.code{
				width: 172rpx;
				margin: auto 0;
				color:$main-color;
			}
		}
		.input-code{
			input{
					flex: 1;
			}		
		}
		.login{
			font-size: 35rpx;
			background-color: $main-color;
			color: white;
			padding: 23rpx 0;
			margin: 70rpx 0;
			&::after{
				border: none;
			}
		}
	}
</style>
