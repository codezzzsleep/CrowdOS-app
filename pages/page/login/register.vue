<template>
	<view class="container container23541">
		<view class="flex flex-wrap diygw-col-24 flex-direction-column items-center flex7-clz">
			<image src="/static/logo.png" class="image3-size diygw-image diygw-col-0 image3-clz" mode="widthFix"></image>
			<view class="diygw-col-0 text1-clz"> 账号注册 </view>
		</view>
		<u-form :model="form" :rules="formRules" :errorType="['message', 'toast']" ref="formRef" class="flex diygw-form diygw-col-24 form-clz">
			<u-form-item :borderBottom="false" class="diygw-col-24 userAccount-clz diygw-form-border" labelPosition="top" prop="userAccount">
				<view class="input solid">
					<text class="diy-icon-mobilefill margin-right-xs" style="color: #636363; font-size: 16px"></text>
					<u-input :focus="formData.userAccountFocus" class="" placeholder="请输入账号" v-model="form.userAccount" type="text"></u-input>
				</view>
			</u-form-item>
			<u-form-item :borderBottom="false" v-if="globalData.logintype != '1'" class="diygw-col-24 userPassword-clz diygw-form-border" labelPosition="top" prop="userPassword">
				<view class="input solid">
					<text class="diy-icon-lock margin-right-xs" style="color: #636363; font-size: 16px"></text>
					<u-input :focus="formData.userPasswordFocus" class="" placeholder="请输入密码" v-model="form.userPassword" type="password" :password-icon="true"></u-input>
				</view>
			</u-form-item>
			<u-form-item :borderBottom="false" v-if="globalData.logintype != '1'" class="diygw-col-24 checkPassword-clz diygw-form-border" labelPosition="top" prop="checkPassword">
				<view class="input solid">
					<text class="diy-icon-lock margin-right-xs" style="color: #636363; font-size: 16px"></text>
					<u-input :focus="formData.checkPasswordFocus" class="" placeholder="请输入确认密码" v-model="form.checkPassword" type="password" :password-icon="true"></u-input>
				</view>
			</u-form-item>
			<view @click="submitForm" class="diygw-col-24 gradual-green text4-clz"> 立即注册 </view>
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
				globalData: { logintype: '0', agree: '0' },
				formRules: {
					userAccount: [
						{
							trigger: ['change', 'blur'],
							required: true,
							message: '账号不能为空'
						}
					],
					userPassword: [
						{
							trigger: ['change', 'blur'],
							required: true,
							message: '密码不能为空'
						}
					],
					checkPassword: [
						{
							trigger: ['change', 'blur'],
							required: true,
							message: '密码不能为空'
						}
					]
				},
				form: {
					userAccount: '',
					userPassword: '',
					checkPassword: ''
				},
				formData: {
					userAccountFocus: false,
					userPasswordFocus: false,
					checkPasswordFocus: false
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
			// 同意或不同意 自定义方法
			async agreeFunction(param) {
				let thiz = this;
				//如果不同意，改为同意
				this.globalData.agree = this.globalData.agree == '1' ? '0' : '1';
			},

			// 验证码登录或密码登录 自定义方法
			async codeFunction(param) {
				let thiz = this;
				//如果1表示验证码登录，0表进密码登录
				this.globalData.logintype = this.globalData.logintype == '1' ? '0' : '1';
			},

			// 发送短信验证码 自定义方法
			async sendMsgFunction(param) {
				let thiz = this;
				this.formData.codeFlag = false;
				if (!this.form.phone) {
					this.showToast('手机号码不能为空');
					//不给发送验证码
					this.formData.codeFlag = false;
					return;
				}
				let pattern = /^1[3-9]\d{9}$/;
				if (!pattern.test(this.form.phone)) {
					this.showToast('手机号码输入有误');
					//不给发送验证码
					this.formData.codeFlag = false;
					return;
				}
				let http_url = '';
				//配置后可删除下面的判断
				if (!http_url) {
					this.showToast('默认发送短信验证地址，配置后可删除此判断');
					return;
				}
				let http_data = {
					phone: this.form.phone
				};
				let http_header = {};
				let data = await this.$http.post(http_url, http_data, http_header, 'json');
				if (data.code == 0) {
					this.showToast(data.msg);
					return;
				} else {
					//修改为true
					this.formData.codeFlag = true;
					this.$refs.codeCodeRef.start();
					this.showToast('验证码已发送');
				}
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
					let url = '/apps/login/login';

					if (this.globalData.agree != '1') {
						this.showToast('请点击同意授权协议');
						return;
					}
					param.logintype = this.globalData.logintype;
					let res = await this.$http.post(url, param, header, 'json');
					if (res.code == 200) {
						this.$session.setUser(res.data);
						this.showToast(res.msg, 'success');
						this.navigateTo({
							type: 'page',
							url: 'index'
						});
					} else {
						this.showToast(res.msg, 'error');
					}
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
	.userAccount-clz {
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
	.userPassword-clz {
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
	.checkPassword-clz {
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
