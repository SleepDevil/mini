<template>
	<view class="wrap">
		<button type="primary" open-type="getUserInfo" @getuserinfo="getUserInfo" v-if="!haveMsg">
			使用微信登录
		</button>
		<view class="topBg">
			<view class="avatar">
				<image :src="avatarUrl" class="userAvatar"></image>
				<text class="userName">{{ username }}</text>
			</view>
		</view>
		<view class="subscribed">
			<view class="mySub">
				<text>我的订阅</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				username: "",
				avatarUrl: "",
				haveMsg: true
			};
		},
		methods: {
			initLogin: function() {
				console.log('initlogin')
				let self = this;
				return new Promise((resolve, reject) => {
					uni.login({
						provider: "weixin",
						success: res => {
							uni.getUserInfo({
								success(res) {
									console.log("**********", res);
									self.username = res.userInfo.nickName;
									self.avatarUrl = res.userInfo.avatarUrl;
									resolve('成功');
								},
								fail() {
									self.haveMsg = false;
								}
							});
						}
					});
				});
			},
			getUserInfo: function(res) {
				let self = this;
				self.username = res.detail.userInfo.nickName;
				self.avatarUrl = res.detail.userInfo.avatarUrl;
				self.haveMsg = true;
			},
			sendUserInfo: function() {
				console.log("sendUserinfo");
				let self = this;
				uni.request({
					method: "POST",
					url: "http://8.136.109.187:8000/adduser",
					data: {
						username: self.username,
						avatarUrl: self.avatarUrl
					},
					success: res => {
						console.log("成功");
						console.log(res);
					}
				});
			}
		},
		async onLoad() {
			await this.initLogin()
			this.sendUserInfo()
		}
	};
</script>

<style>
	.topBg {
		height: 50vh;
		width: 100%;
		background-color: #ff9065;
	}

	.avatar {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 50vh;
	}

	.userAvatar {
		width: 100px;
		height: 100px;
		border-radius: 50%;
	}

	.userName {
		margin-top: 10px;
	}

	.subscribed {
		height: 50vh;
	}

	.mySub {
		display: flex;
		justify-content: center;
	}
</style>
