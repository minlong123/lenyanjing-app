<template>
	<view class="childrendata">
  
		<view class="catelist">
			
			<u-list>
				<u-list-item v-for="(item,index) in resdatas" :key="item.id">
					<u-cell :title="item.title" @click="visitcon(item.id,item.title)">
					</u-cell>
				</u-list-item>
			</u-list>
			
		</view>

	  <u-loading-page loading-text="正在加载中..." :loading="loading"></u-loading-page>
  
	</view>
  </template>
  
  
  <script>
	  

  import { artlis } from "../../basedata/children";
  
  export default {
	data() {
	  return {
		loading:false,
		allcatedata:artlis,
		keyword:"",
		resdatas:"",
	  }
	},
	computed: {
  
	},
	created() {
	},
	onShow() {
	},
	onLoad(options){
		
	  this.id=options.id;
	  this.name=options.title;
	  this.resdatas=this.allcatedata[options.id];
		uni.setNavigationBarTitle({
			title: options.title,
			success: () => {
				console.log('修改标题成功')
			},
			fail: () => {
				console.log('修改标题失败')
			},
			complete: () => {
				console.log('修改标题结束')
			},
		})
	  
	},
	methods: {
		visitcon(id,name){
			// 跳转页面
			uni.navigateTo({
				url: '../detail/index?id='+id+"&title="+name
			});
		},
		getDatas(){
  
		},

		
	  
	},
  }
  </script>
  
  
  <style lang="scss">

  page {
	background-color: #FFFFFF;
  }
  .childrendata{
	  .catelist{
	  	  width:700rpx;
	  	  margin:0 auto;
	  	  display:flex;
	  	  flex-direction:column;
	  	  align-items:flex-start;
		  margin-top:50rpx;
	  	  
	  }
	  .cate-sear{
	  	  width:700rpx;
	  	  margin:0 auto;
	  	  display:flex;
	  	  flex-direction:column;
	  	  
	  }
	  
  }

  
  
  </style>
  