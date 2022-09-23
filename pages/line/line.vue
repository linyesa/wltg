<template>
	<view>
		<view v-for="(tu,index) in list" :index=index :key=index>
			<image class="image-bg" :src="tu.path"></image>
			<view style="text-align: center;"><text>武隆出游 具体景点</text>
			<button type="primary" @click="choose(tu.path)">立即选购</button>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[
					{
						path:"/static/images/t1.jpg"
					},
					{
						path:"/static/images/t2.jpg"
					},
					{
						path:"/static/images/t3.jpg"
					},
					{
						path:"/static/images/t4.jpg"
					},
				],
				
			}
		},
		methods: {
			choose(path){
				uni.navigateTo({
					url:"/pages/xianlu/xianlu?path="+path
				})
			}
			
		}
	}
</script>

<style>
.image-bg{
	width: 100%;
}
</style>
