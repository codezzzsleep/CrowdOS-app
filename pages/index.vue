<template>
	<view class="container container23541">
		<view class="flex flex-wrap diygw-col-24 flex-direction-column flex15-clz">
			<view class="flex diygw-col-24">
				<swiper class="swiper swiper-indicator_rect_radius indicator-right-bottom" indicator-color="rgba(51, 51, 51, 0.39)" indicator-active-color="#fff" indicator-dots="true" autoplay interval="3000" circular="true" style="height: 160px">
					<swiper-item class="diygw-swiper-item">
						<view class="diygw-swiper-item-wrap">
							<image src="/static/p1.png" class="diygw-swiper-image"></image>
						</view>
					</swiper-item>
					<swiper-item class="diygw-swiper-item">
						<view class="diygw-swiper-item-wrap">
							<image src="/static/p2.png" class="diygw-swiper-image"></image>
						</view>
					</swiper-item>
					<swiper-item class="diygw-swiper-item">
						<view class="diygw-swiper-item-wrap">
							<image src="/static/p3.png" class="diygw-swiper-image"></image>
						</view>
					</swiper-item>
				</swiper>
			</view>
		</view>
		<view class="flex flex-wrap diygw-col-24 flex-direction-column flex-clz">
			<view class="flex diygw-col-24 noticebar-clz">
				<diy-noticebar class="flex1 diy-notice-bar" color="#ffffff" bgColor="rgba(160, 157, 157, 0.47)" leftIcon="diy-icon-notification">
					<block v-slot:content>
						<text class="diy-notice-item"> DIY官网做好的拖拽式可视化设计工具 </text>
						<text class="diy-notice-item"> DIY官网做好的拖拽式可视化设计工具 </text>
					</block>
				</diy-noticebar>
			</view>
		</view>
		<view class="flex flex-wrap diygw-col-24 flex5-clz">
			<view class="flex flex-wrap diygw-col-0 flex-direction-column justify-end flex7-clz" @tap="navigateTo" data-type="page" data-url="/pages/page/index/traffic">
				<view class="diygw-col-0"> 人流量查看 </view>
			</view>
			<view class="flex flex-wrap diygw-col-0 flex-direction-column justify-end flex1-clz" @tap="navigateTo" data-type="page" data-url="/pages/page/index/route">
				<view class="diygw-col-0"> 路线规划 </view>
			</view>
		</view>
		<view class="flex flex-wrap diygw-col-24 flex-direction-column items-center flex3-clz">
			<view class="diygw-col-0 text1-clz"> 关于crowd OS </view>
			<view class="flex flex-wrap diygw-col-24 flex-direction-column">
				<view class="diygw-col-24 text-clz"> 1、Crowd OS总体介绍 </view>
				<view class="diygw-col-24 text3-clz"> 一个面向移动众包和群智感知的系统平台 跨平台 CrowdOS适用于Android、iOS、Wear OS等移动操作系统上。 </view>
				<view class="diygw-col-24 text4-clz"> 2、支持多传感器 </view>
				<view class="diygw-col-24 text5-clz"> 它可以调度多个传感器，如重力传感器、方向传感器、陀螺仪传感器、环境光传感器、磁传感器等。 </view>
				<view class="diygw-col-24 text7-clz"> 3、可扩展性 </view>
				<view class="diygw-col-24 text8-clz"> 平台采用模块化设计，具有结构简单，操作方便，易于扩展的特点。 </view>
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
	.flex15-clz {
		margin-left: 20rpx;
		border-bottom-left-radius: 20rpx;
		overflow: hidden;
		width: calc(100% - 20rpx - 20rpx) !important;
		border-top-left-radius: 20rpx;
		margin-top: 20rpx;
		border-top-right-radius: 20rpx;
		border-bottom-right-radius: 20rpx;
		margin-bottom: 20rpx;
		margin-right: 20rpx;
	}
	.flex-clz {
		margin-left: 20rpx;
		border-bottom-left-radius: 20rpx;
		overflow: hidden;
		width: calc(100% - 20rpx - 20rpx) !important;
		border-top-left-radius: 20rpx;
		margin-top: 20rpx;
		border-top-right-radius: 20rpx;
		border-bottom-right-radius: 20rpx;
		margin-bottom: 20rpx;
		margin-right: 20rpx;
	}
	.noticebar-clz {
		top: 0rpx;
		left: 0rpx;
		position: absolute;
	}
	.flex5-clz {
		padding-top: 0rpx;
		z-index: 100;
		color: #ffffff;
		font-weight: bold;
		padding-left: 10rpx;
		font-size: 28rpx !important;
		padding-bottom: 0rpx;
		padding-right: 10rpx;
	}
	.flex7-clz {
		padding-top: 50rpx;
		border-bottom-left-radius: 12rpx;
		z-index: 100;
		background-size: cover;
		padding-left: 20rpx;
		padding-bottom: 20rpx;
		border-top-right-radius: 12rpx;
		background-position: bottom right;
		margin-right: 10rpx;
		margin-left: 10rpx;
		background-repeat: no-repeat;
		overflow: hidden;
		flex: 1;
		border-top-left-radius: 12rpx;
		margin-top: 10rpx;
		border-bottom-right-radius: 12rpx;
		background-image: url(/static/vip.png);
		margin-bottom: 10rpx;
		padding-right: 20rpx;
	}
	.flex1-clz {
		padding-top: 50rpx;
		border-bottom-left-radius: 12rpx;
		z-index: 100;
		background-size: cover;
		padding-left: 20rpx;
		padding-bottom: 20rpx;
		border-top-right-radius: 12rpx;
		background-position: bottom right;
		margin-right: 10rpx;
		margin-left: 10rpx;
		background-repeat: no-repeat;
		overflow: hidden;
		flex: 1;
		border-top-left-radius: 12rpx;
		margin-top: 10rpx;
		border-bottom-right-radius: 12rpx;
		background-image: url(/static/vip2.png);
		margin-bottom: 10rpx;
		padding-right: 20rpx;
	}
	.flex3-clz {
		border: 4rpx dotted #2830fd;
		padding-top: 20rpx;
		border-bottom-left-radius: 20rpx;
		background-size: cover;
		padding-left: 10rpx;
		padding-bottom: 20rpx;
		border-top-right-radius: 20rpx;
		margin-right: 20rpx;
		margin-left: 20rpx;
		overflow: visible;
		width: calc(100% - 20rpx - 20rpx) !important;
		border-top-left-radius: 20rpx;
		margin-top: 40rpx;
		border-bottom-right-radius: 20rpx;
		margin-bottom: 20rpx;
		padding-right: 10rpx;
	}
	.text1-clz {
		background-color: #2830fd;
		margin-left: 10rpx;
		padding-top: 16rpx;
		color: #ffffff;
		font-weight: bold;
		padding-left: 20rpx;
		font-size: 28rpx !important;
		padding-bottom: 16rpx;
		margin-top: -50rpx;
		margin-bottom: 10rpx;
		margin-right: 10rpx;
		padding-right: 20rpx;
	}
	.text-clz {
		margin-left: 10rpx;
		color: #2830fd;
		font-weight: bold;
		width: calc(100% - 10rpx - 10rpx) !important;
		font-size: 28rpx !important;
		margin-top: 10rpx;
		margin-bottom: 10rpx;
		margin-right: 10rpx;
	}
	.text3-clz {
		margin-left: 10rpx;
		width: calc(100% - 10rpx - 10rpx) !important;
		font-size: 28rpx !important;
		margin-top: 0rpx;
		margin-bottom: 10rpx;
		margin-right: 10rpx;
	}
	.text4-clz {
		margin-left: 10rpx;
		color: #2830fd;
		font-weight: bold;
		width: calc(100% - 10rpx - 10rpx) !important;
		font-size: 28rpx !important;
		margin-top: 10rpx;
		margin-bottom: 10rpx;
		margin-right: 10rpx;
	}
	.text5-clz {
		margin-left: 10rpx;
		width: calc(100% - 10rpx - 10rpx) !important;
		font-size: 28rpx !important;
		margin-top: 0rpx;
		margin-bottom: 10rpx;
		margin-right: 10rpx;
	}
	.text7-clz {
		margin-left: 10rpx;
		color: #2830fd;
		font-weight: bold;
		width: calc(100% - 10rpx - 10rpx) !important;
		font-size: 28rpx !important;
		margin-top: 10rpx;
		margin-bottom: 10rpx;
		margin-right: 10rpx;
	}
	.text8-clz {
		margin-left: 10rpx;
		width: calc(100% - 10rpx - 10rpx) !important;
		font-size: 28rpx !important;
		margin-top: 0rpx;
		margin-bottom: 10rpx;
		margin-right: 10rpx;
	}
	.container23541 {
		padding-left: 0px;
		padding-right: 0px;
	}
	.container23541 {
	}
</style>
