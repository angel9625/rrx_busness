<template>
	<view class="tab-bar">
		<slot></slot>
	</view>
</template>

<script>
	export default{
		name:'TabBar'
	}
</script>

<style>
	.tab-bar{
		height: 89upx;
		background-color: red;
		position: absolute;
		left: 0;
		right: 0;
		bottom: 0;
	}
</style>
