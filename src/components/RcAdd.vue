<template>
  <view class="box">
    <view>
      <view>
        <span>书名：</span>
        <input v-model="rcInfo.name" class="info" />
      </view>
      <view>
        <span>译名：</span>
        <input v-model="rcInfo.name_cn" class="info" />
      </view>
      <view>
        <span>作者：</span>
        <input v-model="rcInfo.author" class="info" />
      </view>
      <span>推荐理由：</span>
      <textarea v-model="rcInfo.reason" class="info" />
    </view>
    <view class="msg" v-if="errMsg">
      <text>{{errMsg}}</text>
    </view>
    <view class="btns">
      <button class="btn" type="default" plain @click="onCancel">取消</button>
      <button class="btn" type="primary" plain @click="onSure">确定</button>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      rcInfo: {
        name: undefined,
        name_cn: undefined,
        author: undefined,
        reason: undefined
      },
      errMsg: ""
    };
  },
  props: ["onHide", "onSubmit"],
  methods: {
    onCancel() {
      console.log("click cancel");
      this.$emit("onHide");
    },
    onSure() {
      console.log("click cancel");
      if (!this.rcInfo.name && !this.rcInfo.name_cn) {
        this.errMsg = "书名和译名至少填写一个";
        return;
      }
      this.$emit("onSubmit", this.rcInfo);
      this.$emit("onHide");
      this.rcInfo = {};
    }
  }
};
</script>

<style scoped>
.box {
  width: 100%;
  background-color: #f0ece4;
  padding: 40rpx 20rpx;
  display: flex;
  flex-direction: column;
}
.info {
  margin: 20rpx 0;
  width: 700rpx;
  border: 2rpx solid #eee;
  border-radius: 10rpx;
  padding: 4rpx 0;
  background-color: #ffffff;
}
.msg {
  font-size: 24rpx;
  color: #dc2f02;
}
.btns {
  margin-top: 40rpx;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
.btn {
  width: 200rpx;
  height: 80rpx;
  font-size: 32rpx;
}
</style>
