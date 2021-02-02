<template>
	<view class="content">
		<view class="steps">
			<uni-steps :active="1" activeColor="rgb(252,206,120)"  :options="steps"></uni-steps>
		</view>
		<view class="input-data">
			<view class="flex">
				<text>*</text>
				<label>商家类别</label>
				<input type="text" focus v-model="categoryValue" placeholder="请选择商家类别" placeholder-class="p-class" disabled="true" @blur="checkCategoryValue"/>
				<image src="../../static/images/register/xiala.png" class="select" @click=""></image>
			</view>
			<view class="flex">
				<text>*</text>
				<label>商家分组</label>
				<input type="text" focus v-model="groupValue" placeholder="请选择商家分组" placeholder-class="p-class" disabled="true" @blur="checkGroupValue"/>
				<image src="../../static/images/register/xiala.png" class="select" @click=""></image>
			</view>
			<view class="flex">
				<text>*</text>
				<label>商家名称</label>
				<input type="text" v-model="busnessName" placeholder="请输入名称" placeholder-class="p-class" @blur="checkBusnessName"/>
			</view>
			<view class="flex">
				<text>*</text>
				<label>主营项目</label>
				<input type="text" v-model="mainjob" placeholder="请填写主营项目" placeholder-class="p-class" @blur="checkMainJob"/>
			</view>
			<view class="flex">
				<text>*</text>
				<label>所在地区</label>
				<input type="text" v-model="province" placeholder="省市区" placeholder-class="p-class" @blur="province"/>
			</view>
			<view class="flex">
				<text>*</text>
				<label>商家名称</label>
				<input type="text" v-model="busnessaddress" placeholder="请填写详细地址" placeholder-class="p-class" @blur="checkBusnessAddress"/>
			</view>
			<view class="flex">
				<text>*</text>
				<label>联系人姓名</label>
				<input type="text" v-model="contactname" placeholder="请输入姓名" placeholder-class="p-class" @blur="checkContactName"/>
			</view>
			<view class="flex">
				<text>*</text>
				<label>联系人身份证号</label>
				<input type="idcard" v-model="idcard" placeholder="请输入正确的身份证号" placeholder-class="p-class" @blur="checkIDCard"/>
			</view>
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
				categoryValue:"",
				groupValue:"",
				busnessName:"",
				mainjob:"",
				province:"",
				busnessaddress:"",
				contactname:"",
				idcard:"",
				}
				},
				methods:{
					checkCategoryValue(){},
					checkGroupValue(){},
					checkBusnessName(){},
					checkMainJob(){},
					province(){},
					checkBusnessAddress(){},
					checkContactName(){},
					checkIDCard(){},
				}
				}
</script>

<style lang="scss">
	.content{
		width: 90%;
		margin: 0 auto;
		.steps{
			padding: 50rpx 0;
			background-color: $bg-color;
		}
		.input-data{
			.flex{
				@include primary-flex($justify-content:flex-start);
				.select{
					width: 28rpx;
					height: 28rpx;
				}
				text{
					color: red;
				}
				label{
					margin-right: 40rpx;
				}
				.p-class{
					font-size:$placeholder-fontsize;
				}
			}
		}
	}
</style>
