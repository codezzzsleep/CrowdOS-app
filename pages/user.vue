<template>
	<view class="container container23541">
		<view class="flex flex-wrap diygw-col-24 items-center flex1-clz">
			<image src="/static/202308032016750.png" class="image-size diygw-image diygw-col-0 image-clz" mode="widthFix"></image>
			<view class="flex flex-wrap diygw-col-0 flex-direction-column items-start flex2-clz">
				<view class="diygw-col-0 text1-clz"> 邓志锋 </view>
				<view class="flex flex-wrap diygw-col-0 items-center flex5-clz">
					<image src="/static/zshy.png" class="image2-size diygw-image diygw-col-0" mode="widthFix"></image>
					<view class="diygw-col-0"> 普通用户 </view>
				</view>
			</view>
		</view>
		<view class="flex flex-wrap diygw-col-24 flex-direction-column flex3-clz">
			<view class="diygw-col-0 text4-clz"> 我的账户 </view>
			<view class="flex diygw-col-24">
				<view class="diygw-grid col-4">
					<view @tap="navigateTo" data-type="page" data-url="/pages/page/task/page/taskList" class="diygw-grid-item">
						<view class="diygw-grid-inner grid-item-clz">
							<view class="diygw-grid-icon diygw-avatar grid-icon-clz">
								<image mode="aspectFit" class="diygw-avatar-img" src="/static/plpj.png"></image>
							</view>
							<view class="diygw-grid-title"> 我的任务 </view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="flex flex-wrap diygw-col-24 flex-direction-column flex4-clz">
			<view class="diygw-col-0 text3-clz"> 我的发布 </view>
			<view class="flex diygw-col-24">
				<view class="diygw-grid col-4">
					<view @tap="navigateTo" data-type="page" data-url="/pages/page/task/page/publish" class="diygw-grid-item">
						<view class="diygw-grid-inner grid2-item-clz">
							<view class="diygw-grid-icon diygw-avatar grid2-icon-clz">
								<image mode="aspectFit" class="diygw-avatar-img" src="/static/bj.png"></image>
							</view>
							<view class="diygw-grid-title"> 发布任务 </view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="flex flex-wrap diygw-col-24 flex-direction-column flex6-clz">
			<view class="flex flex-wrap diygw-col-24 items-center">
				<view @tap="navigateTo" data-type="page" data-url="/pages/page/user/page/user" class="diygw-col-0 text7-clz"> 修改个人信息 </view>
				<text class="flex icon3 diygw-col-0 diy-icon-right"></text>
			</view>
		</view>
		<view class="flex diygw-col-24  flex6-clz">
			<button type="warn" @click="userLogout">退出登录</button>
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
			async init() {},
			userLogout(){
				uni.removeStorageSync('currentUser');
				uni.showToast({
				  title: "退出成功",
				  icon: 'success', // 图标，可选值：'success', 'loading', 'none'
				});
				uni.reLaunch({
				  url: '/pages/page/login/login' // 要跳转的页面路径
				});
			}
		}
	};
</script>

<style lang="scss" scoped>
	.flex1-clz {
		margin-left: 20rpx;
		width: calc(100% - 20rpx - 20rpx) !important;
		margin-top: 20rpx;
		margin-bottom: 0rpx;
		margin-right: 20rpx;
	}
	.image-clz {
		margin-left: 10rpx;
		border: 2rpx solid rgba(240, 240, 240, 0.17);
		border-bottom-left-radius: 60rpx;
		box-shadow: 0rpx 2rpx 6rpx rgba(242, 242, 242, 0.49);
		overflow: hidden;
		border-top-left-radius: 60rpx;
		margin-top: 0rpx;
		border-top-right-radius: 60rpx;
		border-bottom-right-radius: 60rpx;
		margin-bottom: 0rpx;
		margin-right: 10rpx;
	}
	.image-size {
		height: 100rpx !important;
		width: 100rpx !important;
	}
	.flex2-clz {
		flex: 1;
	}
	.text1-clz {
		margin-left: 0rpx;
		font-weight: bold;
		font-size: 32rpx !important;
		margin-top: 0rpx;
		margin-bottom: 10rpx;
		text-align: center;
		margin-right: 0rpx;
	}
	.flex5-clz {
		background-color: #dbe4e9;
		padding-top: 0rpx;
		border-bottom-left-radius: 40rpx;
		overflow: hidden;
		padding-left: 0rpx;
		padding-bottom: 0rpx;
		border-top-left-radius: 40rpx;
		border-top-right-radius: 40rpx;
		border-bottom-right-radius: 40rpx;
		padding-right: 6rpx;
	}
	.image2-size {
		height: 40rpx !important;
		width: 40rpx !important;
	}
	.flex3-clz {
		padding-top: 20rpx;
		border-bottom-left-radius: 16rpx;
		padding-left: 20rpx;
		padding-bottom: 20rpx;
		border-top-right-radius: 16rpx;
		margin-right: 20rpx;
		background-color: #ffffff;
		margin-left: 20rpx;
		box-shadow: 0rpx 0rpx 36rpx rgba(142, 137, 137, 0.24);
		overflow: hidden;
		width: calc(100% - 20rpx - 20rpx) !important;
		border-top-left-radius: 16rpx;
		margin-top: 30rpx;
		border-bottom-right-radius: 16rpx;
		margin-bottom: 0rpx;
		padding-right: 20rpx;
	}
	.text4-clz {
		font-weight: bold;
		flex: 1;
		font-size: 28rpx !important;
	}
	.grid-item-clz {
		margin: 0px;
		padding: 10px;
	}
	.grid-icon-clz {
		font-size: calc(40px - 4px) !important;

		width: 40px;
		height: 40px;
	}
	.flex4-clz {
		padding-top: 20rpx;
		border-bottom-left-radius: 16rpx;
		padding-left: 20rpx;
		padding-bottom: 20rpx;
		border-top-right-radius: 16rpx;
		margin-right: 20rpx;
		background-color: #ffffff;
		margin-left: 20rpx;
		box-shadow: 0rpx 0rpx 36rpx rgba(142, 137, 137, 0.24);
		overflow: hidden;
		width: calc(100% - 20rpx - 20rpx) !important;
		border-top-left-radius: 16rpx;
		margin-top: 30rpx;
		border-bottom-right-radius: 16rpx;
		margin-bottom: 0rpx;
		padding-right: 20rpx;
	}
	.text3-clz {
		font-weight: bold;
		flex: 1;
		font-size: 28rpx !important;
	}
	.grid2-item-clz {
		margin: 0px;
		padding: 10px;
	}
	.grid2-icon-clz {
		font-size: calc(30px - 4px) !important;

		width: 30px;
		height: 30px;
	}
	.flex6-clz {
		padding-top: 30rpx;
		border-bottom-left-radius: 16rpx;
		padding-left: 20rpx;
		padding-bottom: 30rpx;
		border-top-right-radius: 16rpx;
		margin-right: 20rpx;
		background-color: #ffffff;
		margin-left: 20rpx;
		box-shadow: 0rpx 0rpx 36rpx rgba(142, 137, 137, 0.24);
		overflow: hidden;
		width: calc(100% - 20rpx - 20rpx) !important;
		border-top-left-radius: 16rpx;
		margin-top: 30rpx;
		border-bottom-right-radius: 16rpx;
		margin-bottom: 0rpx;
		padding-right: 20rpx;
	}
	.text7-clz {
		font-weight: bold;
		flex: 1;
		font-size: 28rpx !important;
	}
	.icon3 {
		font-size: 32rpx;
	}
	.container23541 {
		padding-left: 0px;
		padding-right: 0px;
		background-color: #f4f4f4;
	}
	.container23541 {
	}
</style>
