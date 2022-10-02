<template>
	<view>
		<!-- <view style="display: flex;flex-direction: column;">
			<view style="display: flex;align-items: center;">
				<text style="flex-grow: 1;text-align: center;">全部</text>
				<text style="flex-grow: 1;text-align: center;">未使用</text>
				<text style="flex-grow: 1;text-align: center;">已完成</text>
			</view>
			<view style="background-color: orange;">testatset</view>
		</view> -->
		<uni-collapse  accordion v-model="accordionVal">
				<uni-collapse-item title="全部">
					<view class="content">
						<view style="display: flex;align-items: center;">
							<view style="flex-grow:1;">
								<uni-section class="mb-10" title="武隆豪华两日游" :sub-title="time">
								        <template v-slot:decoration>
								          <view class="decoration"></view>
								        </template>
								      </uni-section>
							</view>
							<view>
								<text style="color: red;">#已完成</text>
							</view>
						</view>
						<view style="display: flex;align-items: center;">
							<view style="flex-grow:1;">
								<uni-section class="mb-10" title="武隆豪华两日游" :sub-title="time">
								        <template v-slot:decoration>
								          <view class="decoration"></view>
								        </template>
								      </uni-section>
							</view>
							<view>
								<text style="color: red;">#已完成</text>
							</view>
						</view>
						<view style="display: flex;align-items: center;">
							<view style="flex-grow:1;">
								<uni-section class="mb-10" title="武隆豪华两日游" :sub-title="time">
								        <template v-slot:decoration>
								          <view class="decoration"></view>
								        </template>
								      </uni-section>
							</view>
							<view>
								<text style="color: red;">#未使用</text>
							</view>
						</view>
					</view>
				</uni-collapse-item>
				<uni-collapse-item title="未使用">
					<view class="content">
						<view style="display: flex;align-items: center;">
							<view style="flex-grow:1;">
								<uni-section class="mb-10" title="武隆豪华两日游" :sub-title="time">
								        <template v-slot:decoration>
								          <view class="decoration"></view>
								        </template>
								      </uni-section>
							</view>
							<view>
								<text style="color: red;">#未使用</text>
							</view>
						</view>
						<view style="display: flex;align-items: center;">
							<view style="flex-grow:1;">
								<uni-section class="mb-10" title="武隆豪华两日游" :sub-title="time">
								        <template v-slot:decoration>
								          <view class="decoration"></view>
								        </template>
								      </uni-section>
							</view>
							<view>
								<text style="color: red;">#未使用</text>
							</view>
						</view>
					</view>
				</uni-collapse-item>
				<uni-collapse-item title="已完成">
					<view class="content">
						<view style="display: flex;align-items: center;">
							<view style="flex-grow:1;">
								<uni-section class="mb-10" title="武隆豪华两日游" :sub-title="time">
								        <template v-slot:decoration>
								          <view class="decoration"></view>
								        </template>
								      </uni-section>
							</view>
							<view>
								<text style="color: red;">#已完成</text>
							</view>
						</view>
						<view style="display: flex;align-items: center;">
							<view style="flex-grow:1;">
								<uni-section class="mb-10" title="武隆豪华两日游" :sub-title="time">
								        <template v-slot:decoration>
								          <view class="decoration"></view>
								        </template>
								      </uni-section>
							</view>
							<view>
								<text style="color: red;">#已完成</text>
							</view>
						</view>
					</view>
				</uni-collapse-item>
			</uni-collapse>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				accordionVal:'0',
				time:"2022/02/02 18:00:01"
			}
		},
		methods: {
			
		},
		onLoad(){
			var t=new Date()
			var month=t.getMonth()+1
			this.time=t.getFullYear()+"/"+month+"/"+t.getDate()+" "+t.getHours()+":"+t.getMinutes()+":"+t.getSeconds()
			console.log(this.time)
		}
	}
</script>

<style lang="scss">
	 $uni-success: #18bc37 !default;
	.mb-10 {
		margin-bottom: 10px;
	}
	.decoration{
	    width: 6px;
	    height: 6px;
		margin-right: 4px;
	    border-radius: 50%;
		background-color: $uni-success;
	}
</style>
