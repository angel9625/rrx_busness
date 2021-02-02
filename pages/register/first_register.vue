<template>
	<view class="content">
		<view class="steps">
			<uni-steps  activeColor="rgb(252,206,120)"  :options="steps"></uni-steps>
		</view>
		<view class="input-data">
			<view class="flex">
				<text>*</text>
				<label>账号名</label>
				<input v-model="username" type="text" maxlength="15" placeholder="5-15位英文,字母,数字" placeholder-class="pclass" @blur="checkUsername"/>
			</view>
			<view class="flex">
				<text>*</text>
				<label>设置登录密码</label>
				<input v-model="password" password="true" maxlength="15" placeholder="6-15位英文,字母,数字" placeholder-class="pclass" @blur="checkPassword"/>
			</view>
			<view class="flex">
				<text>*</text>
				<label>确认密码</label>
				<input v-model="confirmpassword" password="true" maxlength="15" @blur="checkRepassword"/>
			</view>
			<view class="flex">
				<text>*</text>
				<label>手机号</label>
				<input v-model="phone" maxlength="11" @blur="checkPhone"/>
			</view>
			<view class="flex">
				<text>*</text>
				<label class="code">验证码</label>
				<input v-model="code" @blur="checkCode"/>
				<view v-if="isShow" class="sendcode" @click="getCode">发送验证码</view>
				<view v-else class="sendcode showtime"><text>{{codetime+'秒后重试'}}</text></view>
			</view>
		</view>
		<view class="footer">
			<label class="radio"><radio class="form-radio" @click="changestate" :checked="state"></radio></label>
			<label class="agree">我已阅读并同意<text class="blue">《商家入驻协议》</text></label>
			<button class="next" @click="next">下一步</button>
		</view>
	</view>
</template>

<script>
	// 引入步骤条
	import uniSteps from '@/components/uni-steps/uni-steps.vue'
	export default{
		components:{
			uniSteps
		},
		data(){
			return{
				steps:[
					{title:"账号信息"},
					{title:"商家信息"},
					{title:"微信绑定"},
					{title:"提交审核"}
				],
				// 用户名
				username:"",
				usernameresult:false,
				// 密码
				password:"",
				passwordresult:"",
				// 确认密码
				confirmpassword:"",
				confirmpasswordresult:false,
				// 手机号
				phone:"",
				phoneresult:false,
				// 验证码
				code:"",
				coderesult:false,
				// radio状态
				state:false,
				isShow:true,
				codetime:0
			}
		},
		methods:{
			// 设置radio的状态切换
			changestate(){
				this.state = !this.state
			},
			// 校验账户名
			checkUsername(){
			let reg = /[A-z0-9]{5,15}/;
			if(reg.test(this.username)){
				this.usernameresult = true;
			}
			else if(this.username.length < 5){
				uni.showToast({
					title:"账号名长度在5-15位",
					icon:"none"
				})	
				this.usernameresult = false;
			}
			else{
				uni.showToast({
					title:"请输入合法的账户名",
					icon:"none"
				})
				this.usernameresult = false;
			}
			},
			// 校验密码
			checkPassword(){
				let reg = /^[A-z0-9]{6,15}$/;
				if(reg.test(this.password)){
					this.passwordresult = true;
				}
				else if(this.password.length < 6){
					uni.showToast({
						title:"密码长度在6-15位",
						icon:"none"
					})
					this.passwordresult = false;
				}
				else{
					uni.showToast({
						title:"请输入合法的密码",
						icon:"none"
					})
					this.passwordresult = false;
				}
			},
			// 确认密码
			checkRepassword(){
				if(this.password == this.confirmpassword){
					this.confirmpasswordresult = true;
				}
				else{
					uni.showToast({
						title:"两次密码不一致",
						icon:"none"
					})
				}
			},
			// 校验手机号
			checkPhone(){
				let reg = /^1[3-9][0-9]{9}$/;
				if(reg.test(this.phone)){
					this.phoneresult = true;				
				}
				else{
					uni.showToast({
						title:"请输入合法的手机号",
						icon:"none"
					})
					this.phoneresult = false;
				}
			},
			// 校验验证码
			checkCode(){
				if(!this.code || this.code.length != 4){
					uni.showToast({
						title:"请输入合法的验证码",
						icon:"none"
					})
				this.coderesult = false;
				}
				else{
					this.coderesult = true;
				}
			},			
			// 下一步
			next(){
				let result=this.usernameresult&&this.passwordresult&&this.confirmpasswordresult&&this.phoneresult&&this.coderesult;
				if(result){
					if(this.state){
						uni.navigateTo({
							url:"./busness_info"
						})
					}
				}
				else{
					uni.showToast({
						title:"请完善信息",
						icon:"none"
					})
				}
			},
			getCode(){}
		}
	}
</script>

<style lang="scss">
	.content{
		width: 90%;
		margin: 0 auto;
		.steps{
			padding: 40rpx 0;
			background-color: $bg-color;			
		}
		.input-data{
			.flex{
				display: flex;
				padding-top: 60rpx;
				label{
					margin-right: 42rpx;
					font-size:30rpx;
					padding-top: 8rpx;
				}
				text{
					color: red;
				}
				.sendcode{
					color: $main-color;
					font-size: 35rpx;
					width: 210rpx;
				}
				.code{
					width: 150rpx;
				}
				.pclass{
					font-size:$placeholder-fontsize;
					color: gray;
				}
			}
		}
	}
	.footer{
		margin-top: 100rpx;
		background-color: $bg-color;
		.radio{
			margin:0 15rpx;
			radio{
			transform: scale(0.7);
			}
		}
		.agree{
			font-size: 30rpx;
			.blue{
				color: blue;
				font-size: 28rpx;
			}
		}
		.next{
			width: 90%;
			padding:20rpx 0;
			margin:50rpx auto;
			color: white;
			background-color:$main-color;
			&::after{
				border: none;
			}
		}
	}
</style>
