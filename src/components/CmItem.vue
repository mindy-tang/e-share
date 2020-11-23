<template>
    <view class="box">
        <view class="head">
            <text class="name">{{item.user_name}}</text>
            <text class="time">{{item.create_time}}</text>
        </view>
        <view class="h-line" />
        <view class="content">{{item.content}}</view>
    </view>
</template>

<script>

export default {
    props: ["item"]
}
</script>

<style scoped>
.box {
    margin-bottom: 30rpx;
    padding: 0 20rpx;
    /* background-color: #e9edc9; */
    width: 100%;
    display: flex;
    flex-direction: column;
}
.head {
    display: flex;
    flex-direction: row;
}
.name {
    margin-right: 20rpx;
    font-size: 28rpx;
    color: #666;
}
.time {
    font-size: 24rpx;
    color: #999;
}
.content {
    font-size: 28rpx;
}
</style>
