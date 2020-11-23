<template>
  <view class="content">
      <RcAdd 
        v-if="visible" 
        @onHide="visible = false"
        @onSubmit="addRcs"
    />
    <!-- <view v-if="visible">
      <RcAdd />
    </view> -->
    <view v-for="item in rcList" :key="item._id">
      <RcCard :item="item" />
    </view>
    <view v-if="!visible" class="add-btn-box">
      <button class="add-btn" type="dafault" @click="changeVisible">➕</button>
    </view>
  </view>
</template>

<script>
import { Host } from "../const/HttpUtil";
import RcCard from "../components/RcCard";
import RcAdd from "../components/RcAdd";
import moment from 'moment';

const app = getApp();

const addIcon = require("../static/icons/add-white.png");

export default {
  components: {
    RcCard,
    RcAdd
  },
  data() {
    return {
      title: "recomend",
      rcList: [],
      visible: false,
      userInfo:{}
    };
  },
  onLoad() {
    this.getRcs();
    if (app.globalData.userInfo) {
      console.log('userInfo', app.globalData.userInfo);
      
      this.userInfo = app.globalData.userInfo;
    }
  },
  methods: {
    //查询推荐列表
    getRcs() {
      uni.request({
        url: `${Host}/recommend/list`,
        success: res => {
          this.rcList = res.data.map(item => ({
              ...item,
              create_time: moment(item.create_time).format('YYYY/MM/DD')
          }));
        }
      });
    },
    //新增推荐
    addRcs(rc) {
      const param = {
        ...rc,
        user_name: this.userInfo.nickName || '',
        avatar: this.userInfo.avatarUrl || ''
      }
      uni.request({
        method: "POST",
        url: `${Host}/recommend/add`,
        data: rc,
        success: res => {
          console.log("新增推荐成功");
          this.getRcs();
        }
      });
    },
    changeVisible() {
      console.log("click change visible:", this.visible);
      this.visible = !this.visible;
    }
  }
};
</script>

<style scoped>
.add-btn-box {
  position: absolute;
  right: 40rpx;
  bottom: 120rpx;
  font-size: 32rpx;
  color: #ffffff;
}
.add-btn {
  width: 120rpx;
  height: 120rpx;
  border-radius: 60rpx;
  background-color: #8e9c81;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
</style>