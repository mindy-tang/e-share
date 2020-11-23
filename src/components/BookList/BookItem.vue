<template>
  <view class="column box">
    <image class="img" :src="book.cover" />
    <view class="info">
      <text class="name">《{{ book.name }}》</text>
      <text class="name-cn">《{{ book.name_cn }}》</text>
      <text class="author">{{ book.author }}</text>
    </view>
  </view>
</template>

<script>
export default {
  name: "BookItem",
  props: ["book"],
};
</script>

<style scoped>
.box {
  margin: 0 30rpx;
  width: 220rpx;
  height: 460rpx;
  background-color: cadetblue;
}
.img {
  width: 100%;
  height: 300rpx;
}
.info {
  padding: 10rpx;
}
.name {
  margin: 10rpx 0;
  font-size: 32rpx;
}
.name-cn {
  font-size: 24rpx;
  color: #eeeeee;
}
.author {
  font-size: 28rpx;
}
</style>
