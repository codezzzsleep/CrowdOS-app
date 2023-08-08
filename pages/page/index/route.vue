<template>
	<view class="container container23541">
		<view class="diygw-col-24">
			<map style="width: 100%; height: 300px" :latitude="tmap.latitude" @markertap="clickTmapMarker" :longitude="tmap.longitude" :markers="tmap.markers"> </map>
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
				globalData: {},
				tmap: {
					width: 30,
					height: 30,
					latitude: 39.908551757213615,
					longitude: 116.39747754232786,
					markers: [
						{
							id: 0,
							width: 30,
							height: 30,
							latitude: 39.908551757213615,
							longitude: 116.39747754232786,
							callout: {
								content: '北京天安门',
								padding: 10,
								borderRadius: 2,
								display: 'ALWAYS'
							},
							iconPath: '/static/markers.png'
						}
					]
				}
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
			clickTmapMarker(evt) {
				let marker = this.tmap.markers[evt.detail.markerId];
				if (marker && marker.action) {
					this.navigateTo(marker.action);
				}
			}
		}
	};
</script>

<style lang="scss" scoped>
	.container23541 {
		padding-left: 0px;
		padding-right: 0px;
	}
	.container23541 {
	}
</style>
