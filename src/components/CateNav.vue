<template>
  <view class="box">
    <view class="item" v-for="cate in cates" :key="cate.no" @click="onChange(cate)">
      <view class="active_sign" v-show="currentCate.no == cate.no" />
      <text class="item-text" :class="currentCate.no == cate.no?'active':''">
        {{ cate.name }}
      </text>
    </view>
  </view>
</template>

<script>
export default {
  // 书籍类型导航栏
  name: "CateNav",
  props:["cates","currentCate","changeCate"],
  data() {
    return {
      
    };
  },
  methods:{
      onChange(cate){
          this.$emit("changeCate",cate)
      }
  }
};
</script>

<style scoped>
.box {
  height: 100%;
  width: 150rpx;
  border-right: 2rpx solid #eee;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}
.item {
  display: flex;
  flex-direction: row;
  align-items: center;
  height: 80rpx;
  width: 100%;
  margin: 15rpx 0;
  padding: 0 10rpx;
}
.item-text {
  flex: 1;
  text-align: center;
  font-size: 28rpx;
  color: #666;
}
.active_sign {
  width: 10rpx;
  height: 30rpx;
  background-color: #627356;
}
.active {
    color: #627356
}
</style>
