<template>
  <view class="profile-container">
    <view class="profile-header">
      <image class="profile-avatar" src="/static/avatar.png" />
      <text class="profile-name">{{username}}</text>
      <text class="profile-email">{{email}}</text>
    </view>
    <view class="profile-section">
      <text class="profile-section-title">我的信息</text>
      <view class="profile-item" @click="navigateTo('personalInformation')">
        <text>个人信息</text>
        <text class="uni-icon uni-icon-arrowright"></text>
      </view>
      <view class="profile-item" @click="navigateTo('changePassword')">
        <text>修改密码</text>
        <text class="uni-icon uni-icon-arrowright"></text>
      </view>
    </view>
    <view class="profile-section">
      <text class="profile-section-title">设置</text>
      <view class="profile-item" @click="navigateTo('settings')">
        <text>账户设置</text>
        <text class="uni-icon uni-icon-arrowright"></text>
      </view>
      <view class="profile-item" @click="navigateTo('help')">
        <text>帮助与反馈</text>
        <text class="uni-icon uni-icon-arrowright"></text>
      </view>
    </view>
    <button class="logout-button" @click="logout">退出登录</button>
  </view>
</template>

<script>
export default {
  data() {
    return {
      username: '用户',
      email: 'user@example.com',
    };
  },
  methods: {
    navigateTo(page) {
      uni.navigateTo({
        url: `/pages/${page}/${page}`,
      });
    },
    logout() {
      // 添加你的退出登录逻辑
      console.log('Logout');
    },
  },
};
</script>

<style>
.profile-container {
  display: flex;
  flex-direction: column;
  padding: 20rpx;
  background-color: #f5f5f5;
}
.profile-header {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 40rpx 0;
  background-color: #fff;
  margin-bottom: 20rpx;
}
.profile-avatar {
  width: 100rpx;
  height: 100rpx;
  border-radius: 50%;
}
.profile-name {
  margin-top: 20rpx;
  font-size: 32rpx;
  color: #333;
}
.profile-email {
  font-size: 24rpx;
  color: #666;
}
.profile-section {
  margin-bottom: 20rpx;
  background-color: #fff;
}
.profile-section-title {
  padding: 20rpx;
  font-size: 28rpx;
  color: #333;
  border-bottom: 1px solid #eee;
}
.profile-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20rpx;
  border-bottom: 1px solid #eee;
}
.logout-button {
  width: 90%;
  height: 80rpx;
  line-height: 80rpx;
  color: #fff;
  background-color: #f44336;
  text-align: center;
  margin: 20rpx auto;
  border-radius: 4rpx;
}
</style>