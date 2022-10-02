<template>
	<view>
		<view>
			<uni-search-bar placeholder="搜索景点/酒店" bgColor="#EEEEEE" @confirm="search" />
			<swiper class="swiper" circular :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval"
							:duration="duration">
							<swiper-item v-for="(image,index) in imagePath" :key="index" :index="index">
								<image :src="image.path" class="image-bg"></image>
							</swiper-item>
							
						</swiper>
		</view>
		<uni-calendar 
		ref="calendar"
		:insert="false"
		@confirm="confirm"
		:lunar="true"
		 />
		 <view><button type="primary" plain="true" @click="open">选择日期</button></view>
		 <view><uni-grid :column="4" :highlight="true" @change="change">
		 				<uni-grid-item v-for="(value,key,index) in list" :index="index" :key="index">
		 					<view class="grid-item-box" style="background-color: #fff;">
		 						<uni-icons :type="key" :size="90" color="#a4b2ff" />
		 						<text class="text" v-text="value" style="margin-left: 30%;"></text>
		 					</view>
		 				</uni-grid-item>
		</uni-grid>
		</view>
		<view style="margin-top: 20px;">
			<view>1{{foundInfo.scenicName}}</view>
			<view>2{{foundInfo.scenicAddress}}</view>
			<view>3{{foundInfo.scenicDescribe}}</view>
			<image v-if="foundInfo.scenicImage" :src="`${backendURL}/img/show/${foundInfo.scenicImage}`" style="width: 100%;"></image>
		</view>
	</view>
</template>

<script>
	
	export default {
	    data() {
	        return {
				time:"当前时间",
				list:{
					"map-filled":"景点","paperplane-filled":"路线","gift":"周边","home-filled":"酒店"
				},
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500,
				imagePath:[
					{path:"/static/images/long.jpg"},
					{path:"/static/images/t7.jpg"},
					{path:"/static/images/t8.jpg"},
					{path:"/static/images/t9.jpg"},
				],
				foundInfo:{}
			};
	    },
	    methods: {
	        open(){
	            this.$refs.calendar.open();
	        },
	        confirm(e) {
	            console.log(e.fulldate)
	        },
			search(res) {
							uni.showToast({
								title: '搜索：' + res.value,
								icon: 'none'
							})
						},
		    change(e) {
		    		console.log(e.detail.index);
					if(e.detail.index==1){
						console.log("if")
						uni.switchTab({
							url:'/pages/line/line',
							success: (res) => {
								console.log(res);
								console.log("success")
							},
				
						})
					}
		    		},
			fetchFoundInfo() {
				this.$axios({
					method: 'get',
					url: '/index/foundInfo',
				}).then(res => {
					this.foundInfo = res.data;
				}).catch(err => {
					console.log(err)
				})
			},
	    },
		computed:{
			
		},
		mounted(){
			this.fetchFoundInfo()
		}
		
	};
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	.image-bg{
		width: 100%;
		display: block;
		height: 100%;
		line-height: 300rpx;
	}
	.swiper{
			height: 500rpx;	
	}
	
</style>
