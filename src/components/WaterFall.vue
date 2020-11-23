<template>
  <view class="box">
    <view class="left">
      <block v-for="(item, index) in list" :key="index" class="itemlist">
        <view class="card" @click="onClick(item)" v-if="index % 2 == 0">
          <image class="card-img" :src="item.cover" mode="widthFix"></image>
          <view class="info column">
            <text class="name">《{{ item.name }}》</text>
            <text class="name-cn">{{ item.name_cn }}</text>
            <text class="author">{{ item.author }}</text>
          </view>
        </view>
      </block>
    </view>

    <view class="right">
      <block v-for="(item, index) in list" :key="index" class="itemlist">
        <view class="card" @click="onClick(item)" v-if="index % 2 == 1">
          <image class="card-img" :src="item.cover" mode="widthFix"></image>
          <view class="info column">
            <text class="name">《{{ item.name }}》</text>
            <text class="name-cn">{{ item.name_cn }}</text>
            <text class="author">{{ item.author }}</text>
          </view>
        </view>
      </block>
    </view>
  </view>
</template>
<script>
export default {
  name: "WaterFall",
  props: ["list","clickItem"],
  methods: {
    onClick(item) {
      this.$emit("clickItem",item)
    },
  },
};
</script>
<style scope>
.box {
  padding: 10rpx;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
.left,
.right {
  display: inline-block;
  vertical-align: top;
  width: 240rpx;
}

.itemlist {
  background-color: #fff;
  margin: 1%;
  display: inline-block;
}
.card {
  background-color: #f9f9f9;
  margin-bottom: 30rpx;
  /* border: 1rpx solid #eeeeee; */
  border-radius: 20rpx;
  box-shadow: 2rpx rgba(0, 0, 0, 0.5);
}
.card-img {
  width: 100%;
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
  color: #666;
}
.author {
  font-size: 28rpx;
}
</style>
