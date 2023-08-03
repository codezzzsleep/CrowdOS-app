<template>
	<view class="uni-wrap">
		<uni-section class="mb-10" title="热点任务">
					<template v-slot:decoration>
					  <view class="decoration"></view>
					</template>
		</uni-section>
		<uni-section class="mb-10" title="基础任务" type="line"></uni-section>
		<uni-list>
			<uni-list-item title="开启点击反馈" clickable  @click="onClick" ></uni-list-item>
			<uni-list-item title="默认 navigateTo 方式跳转页面" link to="/pages/vue/index/index" @click="onClick($event,1)" ></uni-list-item>
			<uni-list-item title="reLaunch 方式跳转页面" link="reLaunch" to="/pages/vue/index/index" @click="onClick($event,1)" ></uni-list-item>
		</uni-list>
	</view>
</template>

<script>
	export default {
		data() {
			return {
			}
		},
		onReady() {

		},
		methods: {

		}
	}
</script>

<style lang="scss">
  $uni-success: #18bc37 !default;

	.uni-wrap {
		flex-direction: column;
		/* #ifdef H5 */
		height: calc(100vh - 44px);
		/* #endif */
		/* #ifndef H5 */
		height: 100vh;
		/* #endif */
		flex: 1;
	}

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

