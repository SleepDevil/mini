<template>
	<view class="main">
		<view class="withDash">
			<text>{{title}}:</text>
		</view>
		<text class="neirong" v-for="item in categroies" :key="item" @click="$emit('changeCover')">{{item}}</text>
	</view>
</template>

<script>
	export default {
		props: {
			title: String,
			categroies: Array
		}
	}
</script>

<style>
	.main {
		margin-left: 5%;
		width: 85%;
		margin-bottom: 10px;
		margin-top: 10px;
	}
	.withDash {
		border-bottom: 1px dashed #000;
		padding-bottom: 6px;
	}

	.neirong {
		cursor: pointer;
		margin-right: 7px;
		color: red;
		border-bottom: 1px solid red;
	}
</style>
