<template>
	<view class="content">

		<view class="demo-wrap">
			<view id="demo1" class="demo" @click="showTips('demo1','top')">上边提示</view>
			<view id="demo2" class="demo" @click="showTips('demo2','bottom')">下边提示</view>
			<view id="demo3" class="demo" @click="showTips('demo3','left')">左边提示</view>
			<view id="demo4" class="demo" @click="showTips('demo4','right')">右边提示</view>
		</view>

		<bianmarenTooltips
			:gravity="gravity"
			:tooltipShow="tooltipShow"
			:btns="tooltipBtns"
			:eleId="eleId"
			@btnClick="sortTooltipClick"></bianmarenTooltips>
	</view>
</template>

<script>
	
	//组件倒入
	import bianmarenTooltips from '@/components/bianmaren-tooltips/bianmaren-tooltips.vue'
	
	export default {
		components: {bianmarenTooltips},
		data() {
			return {
				//方向
				gravity:'bottom',
				//是否显示
				tooltipShow:false,
				//按钮
				tooltipBtns:["今日","昨日","近一周","近一月"],
				//点击元素
				eleId:""
			}
		},
		onLoad() {
			
		},
		methods: {
			showTips(id,gravity){
				this.tooltipShow = true;
				this.eleId = id;
				this.gravity = gravity;
			},
			sortTooltipClick(btnName){
				uni.showToast({
					title:btnName+"点击",
					icon:'none'
				})
			}
		}
	}
</script>

<style>
	
	.demo-wrap{
		text-align: center;
		padding-top: 100rpx;
	}
	.demo{
		display: inline-block;
			border: #000000 solid 1px;
	}
	
	#demo3{
		position: fixed;
		right: 0;
		top: 50%;
		word-break: break-all;
		width: 25px;
	}
	#demo4{
		position: fixed;
		left: 0;
		top: 50%;
		word-break: break-all;
		width: 25px;
	}
</style>
