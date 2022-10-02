<template>
	<view>
		<button @click="test()">sdakhfalksd</button>
		<button class="button" type="primary" @click="toggle('bottom')"><text class="button-text">底部</text></button>
		<uni-popup ref="popup" background-color="#fff" @change="change" type="bottom">
						<view class="popup-content" style="display: flex;flex-direction: column;height: 50%;">
							<text class="text">费用明细</text>
							<view style="width: 100%;display: flex;flex-grow: 1;">
								<text style="flex-grow: 1">基本费用</text><text>$1999</text>
							</view>
							<view style="width: 100%;display: flex;flex-grow: 1;">
								<text style="flex-grow: 1">成人</text><text>$3999</text>
							</view>
							<view style="width: 100%;display: flex;flex-grow: 1;">
								<text style="flex-grow: 1">儿童</text><text>$8999</text>
							</view><view style="width: 100%;display: flex;flex-grow: 1;">
								<text style="flex-grow: 1;">总额</text><text style="color:red">$435999</text>
							</view>
							<button style="color:#fff;background-color: orange" @click="zhifu">立即支付</button>
						</view>
		</uni-popup>
		<view>
			<uni-collapse  accordion v-model="accordionVal">
				<uni-collapse-item title="手风琴效果">
					<view class="content">
						<text class="text">手风琴效果同时只会保留一个组件的打开状态，其余组件会自动关闭。</text>
					</view>
				</uni-collapse-item>
				<uni-collapse-item title="手风琴效果">
					<view class="content">
						<text class="text">手风琴效果同时只会保留一个组件的打开状态，其余组件会自动关闭。</text>
					</view>
				</uni-collapse-item>
				<uni-collapse-item title="手风琴效果">
					<view class="content">
						<text class="text">手风琴效果同时只会保留一个组件的打开状态，其余组件会自动关闭。</text>
					</view>
				</uni-collapse-item>
			</uni-collapse>
			</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				foundInfo:{},
				accordionVal:'0',
			}
		},
		methods: {
			change(e) {
							console.log('当前模式：' + e.type + ',状态：' + e.show);
						},
			test(){this.$axios({
				method: 'get',
				url: '/index/foundInfo',
			}).then(res => {
				this.foundInfo = res.data;
				console.log(this.foundInfo)
			}).catch(err => {
				console.log(err)
			})
			},
			toggle(type) {
							this.type = type
							// open 方法传入参数 等同在 uni-popup 组件上绑定 type属性
							this.$refs.popup.open(type)
						},
			zhifu(){
				uni.navigateTo(
				{
					url:"/pages/jiesuan/jiesuan"
				})
			},
			changee(e) {
				console.log(e);
			}
			
		}
	}
</script>

<style>
.popup-content {
		@include flex;
		align-items: center;
		justify-content: center;
		padding: 15px;
		height: 50px;
		background-color: #fff;
	}
</style>
