<template>
	<view class="container container23541">
		<view class="flex flex-wrap diygw-col-24">
			<view class="flex flex-wrap diygw-col-12 flex-direction-column flex1-clz">
				<view v-for="(item, index) in globalData.leftList" :key="index" class="flex flex-wrap diygw-col-24 flex-direction-column flex2-clz">
					<image :src="item.img" class="response diygw-col-24 image-clz" mode="widthFix"></image>
					<view class="diygw-text-line2 diygw-col-24 text-clz">
						{{ item.title }}
					</view>
					<view class="diygw-text-line2 diygw-col-24 text2-clz"> {{ item.price }}元 </view>
					<view class="flex flex-wrap diygw-col-24">
						<view v-for="(tagItem, tagIndex) in item.tags" :key="tagIndex" class="diygw-col-0 text1-clz" :class="[tagIndex == 0 ? 'tag-bg' : '']">
							{{ tagItem }}
						</view>
					</view>
					<view class="diygw-text-line2 diygw-col-24 text3-clz">
						{{ item.shop }}
					</view>
				</view>
			</view>
			<view class="flex flex-wrap diygw-col-12 flex-direction-column flex4-clz">
				<view v-for="(item, index) in globalData.rightList" :key="index" class="flex flex-wrap diygw-col-24 flex-direction-column flex5-clz">
					<image :src="item.img" class="response diygw-col-24 image1-clz" mode="widthFix"></image>
					<view class="diygw-text-line2 diygw-col-24 text4-clz">
						{{ item.title }}
					</view>
					<view class="diygw-text-line2 diygw-col-24 text5-clz"> {{ item.price }}元11111 </view>
					<view class="flex flex-wrap diygw-col-24">
						<view v-for="(tagItem, tagIndex) in item.tags" :key="tagIndex" class="diygw-col-0 text6-clz" :class="[tagIndex == 0 ? 'tag-bg' : '']">
							{{ tagItem }}
						</view>
					</view>
					<view class="diygw-text-line2 diygw-col-24 text7-clz">
						{{ item.shop }}
					</view>
				</view>
			</view>
		</view>
		<view class="version text-grey flex-direction-column flex diygw-col-24 justify-center align-center">
			<view> DIY官网代码生成器生成 </view>
			<view> http://www.diygw.com </view>
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
				globalData: { leftList: [], rightList: [] },
				resultNum: 1,
				result: {
					code: 0,
					msg: '',
					rows: [
						{
							title: '',
							shop: '',
							price: 0,
							tags: ['自营', '放心购'],
							img: ''
						}
					]
				}
			};
		},
		computed: {},
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
			async init() {
				await this.resultApi();
			},
			// 无限加载API API请求方法
			async resultApi(param) {
				let thiz = this;
				param = param || {};
				//请求地址及请求数据，可以在加载前执行上面增加自己的代码逻辑
				let http_url = 'https://php.diygw.com/article1.php';
				let http_data = {
					pageNum: this.resultNum,
					pageSize: 10
				};
				let http_header = {};

				let result = await this.$http.post(http_url, http_data, http_header, 'json');

				let datarows = result.rows;
				if (http_data.pageNum == 1) {
					this.result = result;
				} else if (datarows) {
					let rows = this.result.rows.concat(datarows);
					result.rows = rows;
					this.result = result;
				}
				if (datarows && datarows.length > 0) {
					this.resultNum = this.resultNum + 1;
				}
				result.rows.forEach((item, index) => {
					if (index % 2 == 0) {
						this.globalData.leftList.push(item);
					} else {
						this.globalData.rightList.push(item);
					}
				});
			}
		},
		onPullDownRefresh() {
			// 无限加载API API请求方法
			this.resultNum = 1;
			this.resultApi();

			uni.stopPullDownRefresh();
		},
		onReachBottom() {
			// 无限加载API API请求方法
			this.resultApi();
		}
	};
</script>

<style lang="scss" scoped>
	.flex1-clz {
		padding-top: 10rpx;
		padding-left: 10rpx;
		padding-bottom: 10rpx;
		padding-right: 10rpx;
	}
	.flex2-clz {
		padding-top: 10rpx;
		border-bottom-left-radius: 12rpx;
		padding-left: 10rpx;
		padding-bottom: 10rpx;
		border-top-right-radius: 12rpx;
		margin-right: 0rpx;
		margin-left: 0rpx;
		box-shadow: 0rpx 2rpx 12rpx 4px rgba(75, 75, 75, 0.1);
		overflow: hidden;
		width: calc(100% - 0rpx - 0rpx) !important;
		border-top-left-radius: 12rpx;
		margin-top: 0rpx;
		border-bottom-right-radius: 12rpx;
		margin-bottom: 24rpx;
		padding-right: 10rpx;
	}
	.image-clz {
		border-bottom-left-radius: 12rpx;
		overflow: hidden;
		border-top-left-radius: 12rpx;
		border-top-right-radius: 12rpx;
		border-bottom-right-radius: 12rpx;
	}
	.text-clz {
		padding-top: 10rpx;
		font-weight: bold;
		padding-left: 0rpx;
		font-size: 28rpx !important;
		padding-bottom: 10rpx;
		padding-right: 0rpx;
	}
	.text2-clz {
		padding-top: 6rpx;
		color: #ff2a2a;
		font-weight: bold;
		padding-left: 0rpx;
		font-size: 28rpx !important;
		padding-bottom: 6rpx;
		padding-right: 0rpx;
	}
	.text1-clz {
		border: 2rpx solid #07c160;
		padding-top: 10rpx;
		border-bottom-left-radius: 12rpx;
		color: #07c160;
		padding-left: 16rpx;
		padding-bottom: 10rpx;
		border-top-right-radius: 12rpx;
		margin-right: 10rpx;
		margin-left: 0rpx;
		overflow: hidden;
		border-top-left-radius: 12rpx;
		margin-top: 0rpx;
		border-bottom-right-radius: 12rpx;
		margin-bottom: 0rpx;
		padding-right: 16rpx;
	}
	.text3-clz {
		padding-top: 10rpx;
		color: #5f5f5f;
		padding-left: 0rpx;
		padding-bottom: 10rpx;
		padding-right: 0rpx;
	}
	.flex4-clz {
		padding-top: 10rpx;
		padding-left: 10rpx;
		padding-bottom: 10rpx;
		padding-right: 10rpx;
	}
	.flex5-clz {
		padding-top: 10rpx;
		border-bottom-left-radius: 12rpx;
		padding-left: 10rpx;
		padding-bottom: 10rpx;
		border-top-right-radius: 12rpx;
		margin-right: 0rpx;
		margin-left: 0rpx;
		box-shadow: 0rpx 2rpx 12rpx 4px rgba(75, 75, 75, 0.1);
		overflow: hidden;
		width: calc(100% - 0rpx - 0rpx) !important;
		border-top-left-radius: 12rpx;
		margin-top: 0rpx;
		border-bottom-right-radius: 12rpx;
		margin-bottom: 24rpx;
		padding-right: 10rpx;
	}
	.image1-clz {
		border-bottom-left-radius: 12rpx;
		overflow: hidden;
		border-top-left-radius: 12rpx;
		border-top-right-radius: 12rpx;
		border-bottom-right-radius: 12rpx;
	}
	.text4-clz {
		padding-top: 10rpx;
		font-weight: bold;
		padding-left: 0rpx;
		font-size: 28rpx !important;
		padding-bottom: 10rpx;
		padding-right: 0rpx;
	}
	.text5-clz {
		padding-top: 6rpx;
		color: #ff2a2a;
		font-weight: bold;
		padding-left: 0rpx;
		font-size: 28rpx !important;
		padding-bottom: 6rpx;
		padding-right: 0rpx;
	}
	.text6-clz {
		border: 2rpx solid #07c160;
		padding-top: 10rpx;
		border-bottom-left-radius: 12rpx;
		color: #07c160;
		padding-left: 16rpx;
		padding-bottom: 10rpx;
		border-top-right-radius: 12rpx;
		margin-right: 10rpx;
		margin-left: 0rpx;
		overflow: hidden;
		border-top-left-radius: 12rpx;
		margin-top: 0rpx;
		border-bottom-right-radius: 12rpx;
		margin-bottom: 0rpx;
		padding-right: 16rpx;
	}
	.text7-clz {
		padding-top: 10rpx;
		color: #5f5f5f;
		padding-left: 0rpx;
		padding-bottom: 10rpx;
		padding-right: 0rpx;
	}
	.container23541 {
		padding-left: 0px;
		padding-right: 0px;
	}
	.tag-bg {
		background: #07c160 !important;
		color: #fff !important;
	}
	.container23541 {
	}
</style>
