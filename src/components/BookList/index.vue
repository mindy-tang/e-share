<template>
  <view class="column">
    <view class="cate-box">
      <view class="line" />
      <text class="cate-name">{{ cate.name }}</text>
      <view class="line" />
    </view>
    <!-- <view class="row book-box">
      <BookItem v-for="item in books" :key="item.id" :book="item" />
    </view> -->
    <WaterFall :list="books" @clickItem="clickItem"/>
  </view>
</template>

<script>
import BookItem from "./BookItem";
import WaterFall from '../WaterFall';

export default {
  name: "BookList",
  components: {
    BookItem,
    WaterFall
  },
  props: ["cate","books","navToDetail"],
  data() {
    return {
     
    };
  },
  methods:{
    clickItem(item){
      this.$emit("navToDetail",item);
    }
  }
};
</script>

<style scoped>
.box {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: bisque;
}
.cate-box {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}
.cate-name {
  margin: 0 10rpx;
  font-size: 26rpx;
  color: #ddd;
}
.line {
  width: 200rpx;
  height: 2rpx;
  background-color: #eee;
}
.book-box {
  flex-wrap: wrap;
  padding: 20rpx;
  justify-content: center;
  align-items: center;
}
</style>

