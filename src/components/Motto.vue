<template>
    <view class="box">
        <text class="motto">{{motto}}</text>
        <text class="resource">{{resource}}</text>
    </view>
</template>

<script>

export default{
    name: 'Motto',
    props: {

    },
    data(){
        return {
            motto:'Truly my favorite part is to see the kids jumping up and down and they just get so excited.',
            resource:'November'
        }
    }
};
</script>

<style scoped>
    .box {
        margin:20rpx;
        padding: 20rpx;
        width: 540rpx;
        height: 300rpx;
        background-color: #e9edc9;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        color: #666;
    }
    .motto {
        font-size: 36rpx;
    }
    .resource {
        margin-top: 60rpx;
        width: 100%;
        display: flex;
        flex-direction: row;
        justify-content: flex-end;
        font-size: 32rpx;
    }
</style>