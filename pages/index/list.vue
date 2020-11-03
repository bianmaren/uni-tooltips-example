<template>
	<view class="content">
    <block v-for="n in 100" :key="n">
      <view class="demo-row" :id="'item-'+n" @click="showTips('item-'+n,'bottom')" >
        第{{n}}行数据,点击我
      </view>
    </block>
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
    onPageScroll(e){
		  this.tooltipShow = false;
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

	.demo-row{
    line-height: 80rpx;
    background: #fafafa;
    margin-top: 20rpx;
    text-align: center;
	}
</style>
