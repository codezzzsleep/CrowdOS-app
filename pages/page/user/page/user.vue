<template>
	<view class="container container23541">
		<view class="flex flex-wrap diygw-col-24 flex-direction-column justify-center items-center flex-clz">
			<u-navbar titleWidth="500" :isFixed="true" :isSlotTitle="true" title="修改个人信息" backText="返回" backIconColor="#fff" titleColor="inherit" bgColor="bg-none" :backTextStyle="{ color: 'inherit' }" :isHome="true" :isBack="true">
				<template v-slot:title> 修改个人信息 </template>
			</u-navbar>
		</view>
		<u-form :model="form" :rules="formRules" :errorType="['message', 'toast']" ref="formRef" class="flex diygw-form diygw-col-24">
			<u-form-item :borderBottom="false" class="diygw-col-24 userName-clz" labelPosition="top" prop="userName">
				<u-input :focus="formData.userNameFocus" class="" placeholder="用户昵称" v-model="form.userName" type="text"></u-input>
			</u-form-item>
			<u-form-item :borderBottom="false" class="diygw-col-24 oldPassword-clz" labelPosition="top" prop="oldPassword">
				<u-input :focus="formData.oldPasswordFocus" class="" placeholder="请输入原始密码" v-model="form.oldPassword" type="password" :password-icon="true"></u-input>
			</u-form-item>
			<u-form-item :borderBottom="false" class="diygw-col-24 newPassword-clz" labelPosition="top" prop="newPassword">
				<u-input :focus="formData.newPasswordFocus" class="" placeholder="请输入新密码" v-model="form.newPassword" type="password" :password-icon="true"></u-input>
			</u-form-item>
			<u-form-item :borderBottom="false" class="diygw-col-24 input-clz" labelPosition="top" prop="input">
				<u-input :focus="formData.inputFocus" class="" placeholder="请输入确认密码" v-model="form.input" type="password" :password-icon="true"></u-input>
			</u-form-item>
			<view class="flex diygw-col-24 flex-direction-column justify-center button-clz radius">
				<button @click="submitForm" class="diygw-btn black radius button-button-clz">提交</button>
			</view>
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
				globalData: {},
				formRules: {
					userName: [
						{
							trigger: ['change', 'blur'],
							required: true,
							message: '用户名不能为空'
						}
					],
					oldPassword: [
						{
							trigger: ['change', 'blur'],
							required: true,
							message: '原始密码不能为空'
						}
					],
					newPassword: [
						{
							trigger: ['change', 'blur'],
							required: true,
							message: '新密码不能为空'
						}
					],
					input: [
						{
							trigger: ['change', 'blur'],
							required: true,
							message: '确认密码不能为空'
						}
					]
				},
				form: {
					userName: '',
					oldPassword: '',
					newPassword: '',
					input: ''
				},
				formData: {
					userNameFocus: false,
					oldPasswordFocus: false,
					newPasswordFocus: false,
					inputFocus: false
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

				if (valid) {
					//保存数据
					let param = this.form;
					let header = {};
					let url = '';
					if (!url) {
						this.showToast('请先配置表单提交地址', 'none');
						return false;
					}

					let res = await this.$http.post(url, param, header, 'json');

					if (res.code == 200) {
						this.showToast(res.msg, 'success');
					} else {
						this.showModal(res.msg, '提示', false);
					}
				} else {
					console.log('验证失败');
				}
			}
		}
	};
</script>

<style lang="scss" scoped>
	.flex-clz {
		z-index: 100;
		height: 154rpx;
	}
	.userName-clz {
		margin-left: 40rpx;
		border-bottom-left-radius: 12rpx;
		box-shadow: 0rpx 0rpx 60rpx rgba(31, 31, 31, 0.16);
		overflow: hidden;
		width: calc(100% - 40rpx - 40rpx) !important;
		font-size: 28rpx !important;
		border-top-left-radius: 12rpx;
		margin-top: 40rpx;
		border-top-right-radius: 12rpx;
		border-bottom-right-radius: 12rpx;
		margin-bottom: 0rpx;
		margin-right: 40rpx;
	}
	.oldPassword-clz {
		margin-left: 40rpx;
		border-bottom-left-radius: 12rpx;
		box-shadow: 0rpx 0rpx 60rpx rgba(31, 31, 31, 0.16);
		overflow: hidden;
		width: calc(100% - 40rpx - 40rpx) !important;
		font-size: 28rpx !important;
		border-top-left-radius: 12rpx;
		margin-top: 40rpx;
		border-top-right-radius: 12rpx;
		border-bottom-right-radius: 12rpx;
		margin-bottom: 0rpx;
		margin-right: 40rpx;
	}
	.newPassword-clz {
		margin-left: 40rpx;
		border-bottom-left-radius: 12rpx;
		box-shadow: 0rpx 0rpx 60rpx rgba(31, 31, 31, 0.16);
		overflow: hidden;
		width: calc(100% - 40rpx - 40rpx) !important;
		font-size: 28rpx !important;
		border-top-left-radius: 12rpx;
		margin-top: 40rpx;
		border-top-right-radius: 12rpx;
		border-bottom-right-radius: 12rpx;
		margin-bottom: 0rpx;
		margin-right: 40rpx;
	}
	.input-clz {
		margin-left: 40rpx;
		border-bottom-left-radius: 12rpx;
		box-shadow: 0rpx 0rpx 60rpx rgba(31, 31, 31, 0.16);
		overflow: hidden;
		width: calc(100% - 40rpx - 40rpx) !important;
		font-size: 28rpx !important;
		border-top-left-radius: 12rpx;
		margin-top: 40rpx;
		border-top-right-radius: 12rpx;
		border-bottom-right-radius: 12rpx;
		margin-bottom: 0rpx;
		margin-right: 40rpx;
	}
	.button-clz {
		margin-left: 40rpx;
		box-shadow: 0rpx 0rpx 60rpx rgba(31, 31, 31, 0.16);
		overflow: hidden;
		width: calc(100% - 40rpx - 40rpx) !important;
		font-size: 32rpx !important;
		margin-top: 40rpx;
		margin-bottom: 20rpx;
		margin-right: 40rpx;
	}
	.button-button-clz {
		font-size: 17px !important;
		margin: 0px !important;
		padding: 24px !important;
	}
	.container23541 {
		padding-left: 0px;
		padding-right: 0px;
	}
	.container23541 {
	}
</style>
