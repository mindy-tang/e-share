<template>
  <view class="box">
    <textarea v-model="cmInfo.content" class="area" />
    <button class="btn" @click="onSure">确认</button>
  </view>
</template>

<script>
export default {
  data() {
    return {
      cmInfo: {
        content: undefined
      }
    };
  },
  props: ["onSubmit"],
  methods: {
    onSure(){
      this.$emit('onSubmit', this.cmInfo);
      this.cmInfo = {}
    }
  },
};
</script>

<style scoped>
.box {
  margin-bottom: 20rpx;
  padding: 20rpx 40rpx;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-end;
}
.area {
  margin-bottom: 20rpx;
  width: 100%;
  border: 2rpx solid #eeeeee;
  box-shadow: 0 0 0 0.5;
  background-color: #e9edc9;
}
.btn {
  width: 200rpx;
  background-color: #8e9c81;
  font-size: 28rpx;
  color: #ffffff;
}
</style>
