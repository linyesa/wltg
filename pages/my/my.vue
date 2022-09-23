<template>
	<view>
		<button v-show="isShow" class="login-btn" type="primary" @click="getUserInfo">
			微信用户一键登录
		</button>
		<view v-if="!isShow">
			<div>{{userInfo.nickName}}</div>
			<image :src="userInfo.avatarUrl"></image>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				isShow: true,
				userInfo: null
			}
		},
		mounted() {
			let userInfo = uni.getStorageSync('userInfo');
			if(userInfo) {
				if(new Date(userInfo.exp).getTime() < new Date().getTime()) {
					// 说明已经过期了
					uni.removeStorageSync('userInfo')
					this.isShow = true;
				} else {
					this.isShow = false;
					this.userInfo = userInfo;
				}
			}
		},
		methods: {
			getUserInfo() {
				// 展示加载框
				uni.showLoading({
					title: '加载中',
				});
				uni.getUserProfile({
					desc: '登录后可同步数据',
					success: async (obj) => {
						console.log('obj', obj);
						// 调用 action ，请求登录接口
						// await this.login(obj);
						uni.login({
							provider: 'weixin',
							success: (res) => {
								console.log('res-login', res);
								if (res.errMsg == 'login:ok') {
									this.$axios({
										method: 'post',
										url: '/wxLogin',
										data: {
											"avatarUrl": obj.userInfo.avatarUrl,
											"code": res.code,
											"gender": obj.userInfo.gender,
											"nickName": obj.userInfo.nickName
										}
									}).then(res => {
										this.isShow = false;
										this.userInfo = res.data;
										// 设置过期时间
										let now = new Date();
										let ms = now.getTime();
										let exp = new Date(ms+120*1000);
										this.userInfo.exp = exp;
										uni.setStorageSync("userInfo", res.data);
										
									}).catch(err => {
										console.log(err)
									})

								}
							},
						});
					},
					fail: () => {
						uni.showToast({
							title: '授权已取消',
							icon: 'error',
							mask: true,
						});
					},
					complete: () => {
						// 隐藏loading
						uni.hideLoading();
					},
				});
			},
		}
	}
</script>

<style>

</style>
