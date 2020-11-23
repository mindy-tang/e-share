<template>
  <view class="content">
    <CmCard @onSubmit="addComment" />
    <view class="h-blank" />
    <view v-for="item in cmList" :key="item._id">
      <CmItem :item="item" />
    </view>
  </view>
</template>

<script>
import { Host } from "../const/HttpUtil";
import CmCard from "../components/CmCard";
import CmItem from "../components/CmItem";
import moment from "moment";

const app = getApp()

export default {
  components: {
    CmCard,
    CmItem
  },
  data() {
    return {
      cmList: [],
      userInfo: {}
    };
  },
  onLoad() {
    this.getComments();
    if (app.globalData.userInfo) {
        this.userName = app.globalData.userInfo;
    }
  },
  methods: {
    //查询留言列表
    getComments() {
      uni.request({
        url: `${Host}/comment/list`,
        success: res => {
          this.cmList = res.data.map(item => ({
            ...item,
            create_time: moment(item.create_time).format("YYYY/MM/DD")
          }));
        }
      });
    },
    //新增留言
    addComment(comment) {
        const param = {...comment, user_name: this.userName.nickName};
      console.log('param', param);
      
      uni.request({
        method: "POST",
        url: `${Host}/comment/add`,
        data: param,
        success: res => {
          console.log("新增留言成功");
          this.getComments();
        }
      });
    },
  }
};
</script>

<style scoped>
.h-blank {
  width: 100%;
  height: 20rpx;
  background-color: #eeeeee;
}
</style>