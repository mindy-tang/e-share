<template>
  <view class="column">
    <image class="img" :src="book.cover? book.cover : _cover" />
    <view class="title_box">
      <view class="title">《{{book.name}}》 by {{book.author}}</view>
      <view class="detail">{{book.name_cn}}</view>
    </view>
    <view v-if="book.introduction">
      <view class="hBlank" />
      <view class="info">{{book.introduction}}</view>
    </view>
    <view v-if="book.addr">
      <view class="hBlank" />
      <view class="addr">
        <rich-text selectable>{{book.addr}}</rich-text>
      </view>
    </view>
  </view>
</template>

<script>
import { Host } from "../../const/HttpUtil";
const _cover = require("../../static/cover.png");

export default {
  data() {
    return {
      book: {}
    };
  },
  onLoad(option) {
    uni.showLoading({
      title: "加载中"
    });
    const id = option.id;

    uni.request({
      url: `${Host}/book/detail`,
      data: { id },
      success: res => {
        this.book = res.data;
      }
    });
    uni.hideLoading();
  }
};
</script>

<style scoped>
.box {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.hBlank {
  width: 100%;
  height: 40rpx;
  background-color: #f2f6fa;
}
.img {
  height: 800rpx;
}
.title_box {
  widows: 100%;
  padding: 20rpx;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.title {
  font-size: 36rpx;
  font-weight: bold;
}
.detail {
    margin-left: 20rpx;
  font-size: 24rpx;
  color: #666;
}
.info {
  margin: 40rpx;
  /* background-color: #fff; */
  font-size: 32rpx;
}
.addr {
  margin: 40rpx;
  font-size: 28rpx;
  color:#666;
  padding: 20rpx;
} 
</style>