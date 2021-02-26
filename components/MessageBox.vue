<template>
	<view class="main">
		<view class="Box">
			<text>是否订阅该产品？</text>
			<view class="btns">
				<button type="default" size="mini" @click="$emit('changeCover')">取消</button>
				<button type="primary" size="mini" @click="$emit('changeCover')">确定</button>
			</view>
		</view>
	</view>
</template>

<script>
</script>

<style scoped>
	.Box {
		position: fixed;
		width: 60vw;
		height: 14vh;
		top:50%;
		left:50%;
		transform: translate(-50%,-50%);
		background-color: #FFFFFF;
		border-radius: 5px;
		padding: 20px 10px;
		z-index: 5;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: space-between;
	}
	
	.btns {
		margin-top: 15px;
	}
</style>
