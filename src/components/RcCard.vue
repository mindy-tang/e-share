<template>
  <view class="card-box">
    <view class="card-head">
      <view class="avatar">
        <image class="img" />
        <text>{{item.userName}}</text>
      </view>
      <view>{{item.create_time}}</view>
    </view>
    <view class="card-content">
      <text>书名：{{item.name}}</text>
      <text>译名：{{item.name_cn}}</text>
      <text>作者：{{item.author || ""}}</text>
      <text>推荐理由：{{item.reason}}</text>
    </view>
    <view class="h-line" />
    <view class="card-bottom">测试数据</view>
  </view>
</template>

<script>
export default {
  name: "RcCard",
  props: ["item"]
};
</script>

<style scoped>
.card-box {
  margin: 20rpx 40rpx;
  background-color: #ffffff;
  border-radius: 10rpx;
  border: 2rpx solid #eee;
  padding: 30rpx 20rpx;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  box-shadow: 0 0 0 0.5;
}
.card-head {
  padding: 10rpx 10rpx;
  background-color: #e9edc9;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
.avatar {
  display: flex;
  flex-direction: row;
  align-items: center;
  font-size: 36rpx;
}
.img {
  margin-right: 10rpx;
  width: 80rpx;
  height: 80rpx;
  border-radius: 40rpx;
  background-color: #eeeeee;
}
.card-content {
  margin: 20rpx 0;
  padding: 0 10rpx;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  font-size: 28rpx;
}
.card-bottom {
  padding: 0 10rpx;
  font-size: 24rpx;
  color: #999;
}
</style>
