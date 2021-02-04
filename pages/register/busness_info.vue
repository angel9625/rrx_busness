<template>
	<view class="content">
		<!-- 步骤条 -->
		<view class="steps">
			<uni-steps :active="1" activeColor="rgb(252,206,120)"  :options="steps"></uni-steps>
		</view>
		<!-- 输入框 -->
		<view class="input-data">
			<view class="flex">
				<text class="red">*</text>
				<label>商家类别</label>
				<!-- 商家类别下拉选择器 -->
				<picker @change="changeCatogeryValue"  :range="categoryList" :value="index1">
					 <view class="showvalue">{{categoryList[index1]}}
					 </view>
				</picker>
			</view>
			<view class="flex">
				<text class="red">*</text>
				<label>商家分组</label>
				<!-- 商家分组下拉选择器 -->
				<picker @change="changeGroupValue"  :range="groupList" :value="index2">
				 <view class="showvalue">{{groupList[index2]}}
				 </view>
			</picker>
			</view>
			<view class="flex">
				<text class="red">*</text>
				<label>商家名称</label>
				<input type="text" v-model="busnessName" placeholder="请输入名称" placeholder-class="p-class" @blur="checkBusnessName"/>
			</view>
			<view class="flex">
				<text class="red">*</text>
				<label>主营项目</label>
				<input type="text" v-model="mainjob" placeholder="请填写主营项目" placeholder-class="p-class" @blur="checkMainJob"/>
			</view>
			<view class="flex">
				<text class="red">*</text>
				<label>所在地区</label>
				<input type="text" v-model="province" placeholder="省市区" placeholder-class="p-class" @blur="province"/>
			</view>
			<view class="flex">
				<text class="red">*</text>
				<label>商家名称</label>
				<input type="text" v-model="busnessaddress" placeholder="请填写详细地址" placeholder-class="p-class" @blur="checkBusnessAddress"/>
			</view>
			<view class="flex">
				<text class="red">*</text>
				<label>联系人姓名</label>
				<input type="text" v-model="contactname" placeholder="请输入姓名" placeholder-class="p-class" @blur="checkContactName"/>
			</view>
			<view class="flex">
				<text class="red">*</text>
				<label class="idcard">联系人身份证号</label>
				<input type="idcard" v-model="idcard" placeholder="请输入正确的身份证号" placeholder-class="p-class" @blur="checkIDCard"/>
			</view>
		</view>
		<!-- 商家介绍 -->
		<view class="introduce">
			<label>商户简介</label>
			<textarea maxlength="280" placeholder="编辑商户简介~" placeholder-class="p-class"></textarea>
		</view>
		<!-- 商家LOGO -->
		<view class="logo">
			<view class="logo-text">
				<text class="red">*</text>
				<label>商家LOGO</label>
				<text>（建议图片尺寸，大小2M以内）</text>
				<text>0/1</text>
			</view>
			<view class="logo-upload">
				<image src="../../static/images/register/upload-image.png"></image>
				<text>上传照片</text>
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
				categoryList:['餐饮','医疗','教育'],
				groupList:['售前组','售后组','销售组','实施组'],
				index1:0,
				index2:0,
			
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
					changeCatogeryValue(e){
						this.index1 = e.target.value;
					},
					changeGroupValue(e){
						this.index2 = e.target.value;
					}
				}
				}
</script>

<style lang="scss">
	.content{
		@include pri-content();
		.steps{
			padding: 50rpx 0;
			background-color: $bg-color;
		}
		// 输入框区域
		.input-data{
			.flex{
				padding: 30rpx 0;
				@include primary-flex($justify-content:flex-start);
				label{
					font-size:$label-fontsize;
					margin-right: 40rpx;
				}
				.p-class{
					font-size:$placeholder-fontsize;
				}
				.idcard{
					width:270rpx ;					
				}
				.showvalue{
					width: 450rpx;
					font-size: $placeholder-fontsize;
				}
			}
		}
		// 商家LOGO区域
		.logo{
			.logo-upload{
				image{
					width: 120rpx;
					height: 120rpx;
				}
		}
		}
		
		
	}
</style>
