<template>
	<view class="container container23541">
		<view class="flex flex-wrap diygw-col-24 flex-direction-column items-center flex7-clz">
			<image src="/static/logo.png" class="image3-size diygw-image diygw-col-0 image3-clz" mode="widthFix"></image>
			<view class="diygw-col-0 text1-clz"> 基于crowd OS的人流量监测系统 </view>
		</view>
		<u-form :model="form" :rules="formRules" :errorType="['message', 'toast']" ref="formRef" class="flex diygw-form diygw-col-24 form-clz">
			<u-form-item :borderBottom="false" class="diygw-col-24 account-clz diygw-form-border" labelPosition="top" prop="account">
				<view class="input solid">
					<text class="diy-icon-mobilefill margin-right-xs" style="color: #636363; font-size: 16px"></text>
					<u-input :focus="formData.accountFocus" class="" placeholder="请输入账号" v-model="form.account" type="text"></u-input>
				</view>
			</u-form-item>
			<u-form-item :borderBottom="false" class="diygw-col-24 password-clz diygw-form-border" labelPosition="top" prop="password">
				<view class="input solid">
					<text class="diy-icon-lock margin-right-xs" style="color: #636363; font-size: 16px"></text>
					<u-input :focus="formData.passwordFocus" class="" placeholder="请输入密码" v-model="form.password" type="password" :password-icon="true"></u-input>
				</view>
			</u-form-item>
			<view class="flex diygw-col-24 justify-between flex-nowrap flex1-clz">
				<view class="flex flex-wrap diygw-col-0" @tap="navigateTo" data-type="page" data-url="/pages/null" data-redirect="1">
					<view class="diygw-col-0"> 还没有账号？ </view>
					<view @tap="navigateTo" data-type="page" data-url="/pages//page/login/register" class="diygw-col-0 text2-clz"> 注册 </view>
				</view>
			</view>
			<view @click="submitForm" class="diygw-col-24 gradual-green text4-clz"> 登录 </view>
		</u-form>
		
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
				formRules: {
					account: [
						{
							trigger: ['change', 'blur'],
							required: true,
							message: '账号不能为空'
						}
					],
					password: [
						{
							trigger: ['change', 'blur'],
							required: true,
							message: '密码不能为空'
						}
					]
				},
				form: {
					account: '',
					password: ''
				},
				formData: {
					accountFocus: false,
					passwordFocus: false
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
		onReady() {
			this.$refs.formRef?.setRules(this.formRules);
		},
		methods: {
			async init() {
				await this.initResetform();
			},
			
			initResetform() {
				this.initform = JSON.stringify(this.form);
			},
			resetForm() {
				this.form = JSON.parse(this.initform);
			},

			async submitForm(e) {
				let valid = await this.$refs.formRef.validate();
				console.log("submit")
				if (valid) {
					//保存数据
					let param = this.form;
					let header = {};
					let url = 'user/login';

					uni.request({
						url: `https://crowd.zzzsleep.icu/api/user/login`,
						method: 'POST',
					  data: {
					    userAccount:this.form.account,
					    userPassword: this.form.password
					  },
					  header: {
					    'content-type': 'application/json' // 根据实际需求设置请求头
					  },
					  success: function(res) {
						  console.log(res)
						  uni.showToast({
						    title: res.errMsg,
						    icon: 'none', // 图标，可选值：'success', 'loading', 'none'
						  });
					    if(res.data.code == 0){
							console.log(res.data.data)
							let user = res.data.data
							uni.setStorageSync('currentUser', user);
							uni.showToast({
							  title: "登录成功",
							  icon: 'success', // 图标，可选值：'success', 'loading', 'none'
							});
							uni.reLaunch({
							  url: '/pages/index' // 要跳转的页面路径
							});
						}else{
							uni.showToast({
							  title: res.errMsg,
							  icon: 'none', // 图标，可选值：'success', 'loading', 'none'
							});
							
						}
					  },
					  fail: function(err) {
					    uni.showToast({
					      title: err.errMsg,
					      icon: 'none', // 图标，可选值：'success', 'loading', 'none'
					    });
					  }
					});
				} else {
					uni.showToast({
					  title: "数据格式错误",
					  icon: 'none', // 图标，可选值：'success', 'loading', 'none'
					});
				}
			}
		}
	};
</script>

<style lang="scss" scoped>
	.flex7-clz {
		padding-top: 80rpx;
		border-bottom-left-radius: 40rpx;
		background-size: 100% 100%;
		overflow: hidden;
		padding-left: 10rpx;
		padding-bottom: 60rpx;
		border-top-left-radius: 0rpx;
		border-top-right-radius: 0rpx;
		border-bottom-right-radius: 40rpx;
		background-image: url(/static/mbz704.png);
		background-position: bottom center;
		padding-right: 10rpx;
	}
	.image3-clz {
		flex-shrink: 0;
		border-bottom-left-radius: 120rpx;
		overflow: hidden;
		width: 120rpx !important;
		border-top-left-radius: 120rpx;
		border-top-right-radius: 120rpx;
		border-bottom-right-radius: 120rpx;
		height: 120rpx !important;
	}
	.image3-size {
		height: 120rpx !important;
		width: 120rpx !important;
	}
	.text1-clz {
		margin-left: 10rpx;
		padding-top: 10rpx;
		font-weight: bold;
		padding-left: 20rpx;
		font-size: 32rpx !important;
		padding-bottom: 10rpx;
		margin-top: 0rpx;
		margin-bottom: 10rpx;
		margin-right: 10rpx;
		padding-right: 20rpx;
	}
	.form-clz {
		padding-top: 30rpx;
		border-bottom-left-radius: 12rpx;
		padding-left: 10rpx;
		padding-bottom: 30rpx;
		border-top-right-radius: 12rpx;
		margin-right: 30rpx;
		background-color: #ffffff;
		margin-left: 30rpx;
		overflow: hidden;
		width: calc(100% - 30rpx - 30rpx) !important;
		border-top-left-radius: 12rpx;
		margin-top: 30rpx;
		border-bottom-right-radius: 12rpx;
		margin-bottom: 30rpx;
		padding-right: 10rpx;
	}
	.account-clz {
		margin-left: 10rpx;
		padding-top: 0rpx;
		padding-left: 0rpx;
		width: calc(100% - 10rpx - 10rpx) !important;
		font-size: 28rpx !important;
		padding-bottom: 0rpx;
		margin-top: 10rpx;
		margin-bottom: 10rpx;
		margin-right: 10rpx;
		padding-right: 0rpx;
	}
	.password-clz {
		margin-left: 10rpx;
		padding-top: 0rpx;
		padding-left: 0rpx;
		width: calc(100% - 10rpx - 10rpx) !important;
		font-size: 28rpx !important;
		padding-bottom: 0rpx;
		margin-top: 10rpx;
		margin-bottom: 10rpx;
		margin-right: 10rpx;
		padding-right: 0rpx;
	}
	.flex1-clz {
		margin-left: 10rpx;
		padding-top: 16rpx;
		padding-left: 30rpx;
		width: calc(100% - 10rpx - 10rpx) !important;
		padding-bottom: 16rpx;
		margin-top: 10rpx;
		margin-bottom: 10rpx;
		margin-right: 10rpx;
		padding-right: 30rpx;
	}
	.text2-clz {
		color: #39b54a;
	}
	.text4-clz {
		padding-top: 20rpx;
		border-bottom-left-radius: 120rpx;
		color: #ffffff;
		font-weight: bold;
		letter-spacing: 6rpx !important;
		padding-left: 10rpx;
		font-size: 32rpx !important;
		padding-bottom: 20rpx;
		border-top-right-radius: 120rpx;
		margin-right: 30rpx;
		margin-left: 30rpx;
		box-shadow: 0rpx 6rpx 14rpx rgba(64, 195, 3, 0.35);
		overflow: hidden;
		width: calc(100% - 30rpx - 30rpx) !important;
		border-top-left-radius: 120rpx;
		margin-top: 10rpx;
		border-bottom-right-radius: 120rpx;
		margin-bottom: 10rpx;
		text-align: center;
		padding-right: 10rpx;
	}
	.container23541 {
		padding-left: 0px;
		padding-right: 0px;

		background-position: top center;
		background-size: contain;
		background-repeat: no-repeat;
	}
</style>
