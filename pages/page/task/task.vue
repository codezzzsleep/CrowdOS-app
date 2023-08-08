<template>
	<view class="container container23541">
		<view class="flex flex-wrap diygw-col-24 flex-direction-column items-center flex2-clz">
			<view class="diygw-col-0 text3-clz"> </view>
			<view class="diygw-col-0 text12-clz"> 独享经济型 </view>
			<view class="diygw-col-0 text2-clz"> 热销 </view>
			<view class="flex flex-wrap diygw-col-0 justify-center items-center flex3-clz">
				<view class="diygw-col-0 text5-clz"> 199 </view>
				<view class="diygw-col-0"> /月 </view>
			</view>
			<view class="flex flex-wrap diygw-col-24 justify-between items-center flex8-clz">
				<view class="diygw-col-0"> 网页空间 </view>
				<view class="diygw-col-0 text16-clz"> 1G+赠送200M </view>
			</view>
			<view class="flex flex-wrap diygw-col-24 justify-between items-center flex5-clz">
				<view class="diygw-col-0"> 每月流量 </view>
				<view class="diygw-col-0 text9-clz"> 100G </view>
			</view>
			<view class="flex flex-wrap diygw-col-24 justify-between items-center flex4-clz">
				<view class="diygw-col-0"> 数据库 </view>
				<view class="diygw-col-0 text7-clz"> MYSQL </view>
			</view>
			<view class="flex flex-wrap diygw-col-24 justify-between items-center flex6-clz">
				<view class="diygw-col-0"> 机房线路 </view>
				<view class="diygw-col-0 text11-clz"> 国内BGP/双线机房 </view>
			</view>
			<view class="flex flex-wrap diygw-col-24 justify-between items-center flex9-clz">
				<view class="diygw-col-0 text15-clz"> 查看详情 </view>
				<view class="diygw-col-0 text14-clz"> 立即购买 </view>
			</view>
		</view>
		
		<view class="clearfix"></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				//用户全局信息
				userInfo: {},
				//页面传参
				globalOption: {},
				//自定义全局变量
				globalData: {}
			};
		},
		onShow() {
			this.setCurrentPage(this);
		},
		onLoad(option) {
			this.setCurrentPage(this);
			if (option) {
				this.setData({
					globalOption: this.getOption(option)
				});
			}

			this.init();
		},
		methods: {
			async init() {}
		}
	};
</script>

<style lang="scss" scoped>
	.flex2-clz {
		border: 2rpx solid #fab2b2;
		padding-top: 0rpx;
		padding-left: 20rpx;
		font-size: 28rpx !important;
		padding-bottom: 20rpx;
		margin-right: 20rpx;
		margin-left: 20rpx;
		box-shadow: 0rpx 0rpx 18rpx rgba(250, 178, 178, 0.27);
		overflow: hidden;
		width: calc(100% - 20rpx - 20rpx) !important;
		margin-top: 20rpx;
		margin-bottom: 20rpx;
		padding-right: 20rpx;
	}
	.text3-clz {
		border-top: 120rpx solid #fc5531;
		top: -2rpx;
		border-left: 120rpx solid rgba(255, 255, 255, 0);
		position: absolute;
		right: -2rpx;
	}
	.text12-clz {
		margin-left: 16rpx;
		font-weight: bold;
		font-size: 30rpx !important;
		margin-top: 16rpx;
		margin-bottom: 16rpx;
		text-align: center;
		margin-right: 16rpx;
	}
	.text2-clz {
		color: #ffffff;
		top: 14rpx;
		font-weight: bold;
		font-size: 28rpx !important;
		position: absolute;
		right: 10rpx;
	}
	.flex3-clz {
		border: 2rpx solid #eee;
		border-bottom-left-radius: 200rpx;
		border-top-right-radius: 200rpx;
		margin-right: 10rpx;
		margin-left: 10rpx;
		flex-shrink: 0;
		overflow: hidden;
		width: 200rpx !important;
		border-top-left-radius: 200rpx;
		margin-top: 10rpx;
		border-bottom-right-radius: 200rpx;
		margin-bottom: 10rpx;
		height: 200rpx !important;
	}
	.text5-clz {
		font-weight: bold;
		font-size: 36rpx !important;
	}
	.flex8-clz {
		margin-left: 16rpx;
		padding-top: 16rpx;
		padding-left: 16rpx;
		width: calc(100% - 16rpx - 16rpx) !important;
		padding-bottom: 16rpx;
		margin-top: 16rpx;
		margin-bottom: 0rpx;
		border-bottom: 2rpx solid #eee;
		margin-right: 16rpx;
		padding-right: 16rpx;
	}
	.text16-clz {
		font-weight: bold;
	}
	.flex5-clz {
		margin-left: 16rpx;
		padding-top: 16rpx;
		padding-left: 16rpx;
		width: calc(100% - 16rpx - 16rpx) !important;
		padding-bottom: 16rpx;
		margin-top: 16rpx;
		margin-bottom: 0rpx;
		border-bottom: 2rpx solid #eee;
		margin-right: 16rpx;
		padding-right: 16rpx;
	}
	.text9-clz {
		font-weight: bold;
	}
	.flex4-clz {
		margin-left: 16rpx;
		padding-top: 16rpx;
		padding-left: 16rpx;
		width: calc(100% - 16rpx - 16rpx) !important;
		padding-bottom: 16rpx;
		margin-top: 16rpx;
		margin-bottom: 0rpx;
		border-bottom: 2rpx solid #eee;
		margin-right: 16rpx;
		padding-right: 16rpx;
	}
	.text7-clz {
		font-weight: bold;
	}
	.flex6-clz {
		margin-left: 16rpx;
		padding-top: 16rpx;
		padding-left: 16rpx;
		width: calc(100% - 16rpx - 16rpx) !important;
		padding-bottom: 16rpx;
		margin-top: 16rpx;
		margin-bottom: 0rpx;
		border-bottom: 2rpx solid #eee;
		margin-right: 16rpx;
		padding-right: 16rpx;
	}
	.text11-clz {
		font-weight: bold;
	}
	.flex9-clz {
		margin-left: 16rpx;
		width: calc(100% - 16rpx - 16rpx) !important;
		margin-top: 16rpx;
		margin-bottom: 0rpx;
		margin-right: 16rpx;
	}
	.text15-clz {
		border: 2rpx solid #a9a9a9;
		padding-top: 10rpx;
		color: #7e7d7d;
		font-weight: bold;
		padding-left: 10rpx;
		padding-bottom: 10rpx;
		margin-right: 10rpx;
		margin-left: 10rpx;
		flex: 1;
		margin-top: 10rpx;
		margin-bottom: 10rpx;
		text-align: center;
		padding-right: 10rpx;
	}
	.text14-clz {
		border: 2rpx solid #fc5531;
		padding-top: 10rpx;
		color: #fc5531;
		font-weight: bold;
		padding-left: 10rpx;
		padding-bottom: 10rpx;
		margin-right: 10rpx;
		margin-left: 10rpx;
		flex: 1;
		margin-top: 10rpx;
		margin-bottom: 10rpx;
		text-align: center;
		padding-right: 10rpx;
	}
	.container23541 {
		padding-left: 0px;
		padding-right: 0px;
	}
	.container23541 {
	}
</style>
