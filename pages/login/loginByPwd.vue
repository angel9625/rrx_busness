<template>
	<view class="container">
		<view class="logo">
			<image :src="logo"></image>
		</view>
		<view class="content">
			<view class="login-data">
				<view class="login-input">
					<image :src="phone"></image>
					<input type="text" v-model="username" placeholder="账号/手机号" @blur="checkUsername"/>
				</view>
				<view class="login-input">
					<image :src="pwd"></image>
					<input password="true" v-model="password" placeholder="请输入密码" @blur="checkpassword"/>
				</view>
				<view class="login-button">
					<button class="button-login"  @click="toLogin">登录</button>
					<button class="button-register" @click="toJoin">申请入驻</button>
				</view>
			</view>
			<view class="login-type">
				<text>更多登录方式</text>
				<view class="image" :style="{'background-image': 'url('+nopwd +')'}" @click="toNoPwd"></view>
				<text class="nopsd">免密登录</text>
			</view>
		</view>
	</view>
</template>

<script>
	import logo from '../../static/images/login/logo.png'
	import phone from '../../static/images/login/phone.png'
	import pwd from '../../static/images/login/pwd.png'
	import nopwd from '../../static/images/login/nopwd.png'
	
	export default{
		data(){
			return{
				logo:logo,
				phone:phone,
				pwd:pwd,
				nopwd:nopwd,
				username:"",
				password:"",
			}
		},
		methods:{
			// 校验账户名
			checkUsername(){
				if(!this.username){
					uni.showToast({
						title:"账户名不能为空",
						icon:"none"
					})
				}				
			},
			
			checkpassword(){
				if(!this.password){
					uni.showToast({
						title:"密码不能为空",
						icon:"none"
					})
				}
			},
			// 登录
			toLogin(){
				if(!this.username && !this.password){
					uni.showToast({
						title:"账户名和密码不能为空",
						icon:"none",
					})}
					else{
					uni.switchTab({
						url:'/pages/order/order'
					})
					}
			},
			// 注册
			toJoin(){
				uni.navigateTo({
					url:"../register/index"
				})			
			},
			// 免密登录
			toNoPwd(){
				uni.navigateTo({
					url:"./loginByNoPwd"
				})
			}
		}
	}
	
</script>

<style lang="scss">
	.logo{
		width:330rpx;
		margin:0 auto;
		image{
			width: 330rpx;
			height: 225rpx;
			padding: 90rpx 0 50rpx 0;
		}
	}
	.login-input{
		display: flex;
		width: 80%;
		margin: 10rpx auto;
		border-bottom:rgb(235,232,232) solid 3rpx;
		input{
			font-size: 35rpx;	
			margin: 30rpx 0;
		}
		image{
			width: 30rpx;
			height: 35rpx;
			margin: 30rpx 40rpx 50rpx 0;
		}
	}
	.login-button{
		width: 80%;
		font-size: 35rpx;
		margin: 70rpx auto;
		border: 0;
		button{
			padding: 30rpx;
			margin-bottom: 30rpx;
		}
		.button-login{
			padding: 30rpx;
			color: white;
			background-color:$main-color;
			// 去除边框默认样式
			&::after{ 
				border: none;			
				 }
		}
		.button-register{
			 color:$main-color;
			&::after{
				border: none;
				border: 1rpx solid $main-color;
				 }
		}
	}
.login-type{
	width: 80%;
	display: flex;
	font-size: 35rpx;
	color: rgb(154,154,154);
	text-align: center;
	flex-direction: column;
	margin: 70rpx auto;
	.image{
		width:50rpx ;
		height: 50rpx;
		margin: 30rpx auto;
		background-size: 50rpx 50rpx
	}
	.nopsd{
		font-size: 20rpx;
	}
}
</style>
