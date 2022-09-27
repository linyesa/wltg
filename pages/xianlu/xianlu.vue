<template>
	<view>
		<image class="image-bg" :src="path"></image>
		<view class="big">
		<view class="wen" style="font-size: 1.5rem;margin-left: 5px;">武隆具体景点旅游详情页</view>
		<view class="jia">$399</view>
		<view class="shi">$199</view>
		</view>
		<view>
			<checkbox-group>
					<label v-for="(value,index) in list" :key="index" :index="index">
						<checkbox  checked="true" color="#9c9c9c" style="transform:scale(0.7)" disabled="true"/><text style="font-size: 1rem;">{{value}}</text>
					</label>
				</checkbox-group>
		</view>
		<view style="display: flex;">
			<text style="color:darkgrey;margin-left: 5px;">重庆工程学院品质保证,不好玩不要钱</text>
		</view>
		<view style="display: flex;margin-top: 20px;">
			<view style="background-color: orange; width:10rpx;height: 50rpx;"></view>
			<text>出发时间</text>
		</view>
		<view style="display: flex;margin-top: 20px;">
			<view style="background-color: orange; width:10rpx;height: 50rpx;"></view>
			<text>预定须知</text>
		</view>
		<view style="display:flex;flex-direction: column;" class="tishi">
			<text>预定时间：<text class="nei">最晚需要在出行前1天23：59前购买</text></text>
			<text>退改政策：<text class="nei">使用日期前1天12：00（含）之前，损失费用0%；使用日期前1天12：00之后，损失费用100%；订单不支持部分退</text></text>
			<text>如需改期：<text class="nei">请申请取消后重新预定，紧急联系电话：10086</text></text>
			<text>使用条件：<text class="nei">大小同价</text></text>
		</view>
		<view style="display: flex;margin-top: 20px;">
			<view style="background-color: orange; width:10rpx;height: 50rpx;"></view>
			<text>线路详情</text>
		</view>
		<text style="font-size: 1.5px;">Day01</text>
		<uni-section title="纵向排列" type="line" padding>
					<uni-steps :options="list2" active-color="#007AFF" :active="active" direction="column" />
		</uni-section>
		<text style="font-size: 1.5px;">Day02</text>
		<uni-section title="纵向排列" type="line" padding>
					<uni-steps :options="list2" active-color="#007AFF" :active="active" direction="column" />
		</uni-section>
		<view style="display: flex;margin-top: 20px;">
			<view style="background-color: orange; width:10rpx;height: 50rpx;"></view>
			<text>费用说明</text>
		</view>
		<view><text class="zhengwen">详细说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明费用说明</text></view>
		<view style="display: flex;margin-top: 20px;">
			<view style="background-color: orange; width:10rpx;height: 50rpx;"></view>
			<text>其他说明</text>
		</view>
		<view><text class="zhengwen">是吗是吗是吗是吗是吗说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明说明</text>
		</view>
		<uni-goods-nav :fill="true" :options="options" :button-group="customButtonGroup" @click="onClick"
						@buttonClick="buttonClick" v-if="flag" />
		<uni-popup ref="popup" background-color="#fff" @change="change" type="bottom">
						<view class="popup-content" style="display: flex;flex-direction: column;height: 50%;">
							<text class="text" style="text-align: center;">费用明细</text>
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
							<button style="color:#fff;background-color: orange;" @click="zhifu">立即支付</button>
						</view>
		</uni-popup>
	    
	</view>
</template>

<script>
	export default {
		data() {
			return {
				type:"center",
				active:0,
				list:[
					"品质保证",
					"重庆第一",
					"出行首选",
					"无内购"
				],
				list2: [{
									title: '武隆集合',
									desc: '2018-11-11'
								}, {
									title: '前往balabalabala',
									desc: '2018-11-12'
								}, {
									title: '前往balabala',
									desc: '2018-11-13'
								}, {
									title: '前往bala',
									desc: '2018-11-14'
								}],
				path:"/static/images/chu.jpg",
				options: [{
									icon: 'chat',
									text: '客服'
								}, {
									icon: 'shop',
									text: '店铺',
									info: 2,
									infoBackgroundColor: '#007aff',
									infoColor: "#f5f5f5"
								}, {
									icon: 'cart',
									text: '购物车',
									info: 2
								}],
				customButtonGroup: [{
										text: '加入购物车',
										backgroundColor: 'linear-gradient(90deg, #1E83FF, #0053B8)',
										color: '#fff'
									},
									{
										text: '立即购买',
										backgroundColor: 'linear-gradient(90deg, #60F3FF, #088FEB)',
										color: '#fff'
									}
								],
				flag:true,
				
			}
		},
		methods: {
			onClick(e) {
							uni.showToast({
								title: `点击${e.content.text}`,
								icon: 'none'
							})
						},
			buttonClick(e) {
							console.log(e)
							if(e.index==0){
								this.options[2].info++
							}
							else if(e.index==1){
								console.log("lijigoumai")
								this.flag=false
								this.toggle("bottom")
							}
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
			change(e) {
							console.log('当前模式：' + e.type + ',状态：' + e.show);
						},
		
		},
		onLoad(option){
			this.path=option.path
		}
	}
</script>

<style>
.image-bg{
	width: 100%;
}

.big{
	display: flex;
	flex-direction: row;
	flex-wrap: wrap;
}
.wen{
	flex:1;
	
	
}
.jia{
	color: gray;
	text-decoration: line-through;
	font-size: 50%;
}
.shi{
	color:red;
	font-weight: bold;
	
}
.tishi .nei{
	color:darkgray
}
.tishi text{
	font-size: 1.5px;
}
.zhengwen{
	color:darkgray;
	font-size: 1.5px;
}
</style>
