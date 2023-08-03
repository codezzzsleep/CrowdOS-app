<template>
  <view class="uni-common-mt uni-bg-color">
    <view class="uni-padding-wrap uni-text-center">
      <image class="logo" src="/static/logo.png" />
      <input class="uni-inputs" type="text" v-model="username" placeholder="用户名" />
      <input class="uni-inputs" type="password" v-model="password" placeholder="密码" />
      <button class="uni-btn" @click="login">登录</button>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: '',
    };
  },
  methods: {
    login() {
      if (this.username === '' || this.password === '') {
        uni.showToast({
          title: '用户名和密码不能为空',
          icon: 'none',
        });
        return;
      }
      // 这里可以添加你的登录逻辑代码，例如发送一个API请求到后端
      console.log(`Username: ${this.username}, Password: ${this.password}`);
    },
  },
};
</script>

<style>
.uni-common-mt {
  margin-top: 20rpx;
}
.uni-bg-color {
  background-color: #ffffff;
}
.uni-padding-wrap {
  padding: 20rpx;
}
.uni-text-center {
  text-align: center;
}
.logo {
  width: 128rpx;
  height: 128rpx;
}
.uni-inputs {
  width: 600rpx;
  height: 80rpx;
  line-height: 80rpx;
  padding: 0 20rpx;
  border-radius: 4rpx;
  border: 1px solid #c8c7cc;
  margin: 20rpx auto;
}
.uni-btn {
  width: 600rpx;
  height: 80rpx;
  line-height: 80rpx;
  background-color: #007aff;
  color: #ffffff;
  margin: 20rpx auto;
  border-radius: 4rpx;
}
</style>