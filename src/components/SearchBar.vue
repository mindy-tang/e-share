<template>
    <view class="searchBar">
        <input 
            class="uni-input searchInput" 
            type="text" 
            placeholder-style="color:#cccccc"
            :placeholder="placeholder"
            @confirm="search"
        />
    </view>
</template>

<script>

export default{
    // 搜索框
    name: "SearchBar",
    props: ["queryBook"],
    data(){
        return {
            placeholder:'搜索书名/作者名'
        }
    },
    methods:{
        search(event){
            this.$emit("queryBook",event.target.value);
        }
    }
};
</script>

<style scoped>
    .searchBar {
        margin: 10rpx 15rpx;
        height: 80rpx;
        width: 700rpx;
        background-color: #f9f9f9;
        /* border: 1px solid #c3c3c3; */
        text-align: center;
        font-size: 24rpx;
        border-radius: 4px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    .searchInput {
        flex: 1;
        color: #cccccc
    }
</style>