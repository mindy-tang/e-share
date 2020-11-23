<template>
  <view class="content">
    <SearchBar @queryBook="queryBook" />
    <View class="h-line" />
    <view class="row">
      <CateNav :cates="cates" :currentCate="currentCate" @changeCate="changeCate" />
      <view class="column">
        <Motto />
        <BookList :books="books" :cate="currentCate" @navToDetail="navToDetail"/>
      </view>
    </view>
  </view>
</template>

<script>
import {Host} from "../../const/HttpUtil";
import SearchBar from "../../components/SearchBar";
import CateNav from "../../components/CateNav";
import Motto from "../../components/Motto";
import BookList from "../../components/BookList/index";

export default {
  data() {
    return {
      cates: [],
      books: [],
      currentCate: {}
    };
  },
  components: {
    SearchBar,
    CateNav,
    Motto,
    BookList
  },
  onLoad() {
    //查询全部分类
    uni.request({
      url: `${Host}/cate/list`,
      success: res => {
        this.cates = res.data;
        this.currentCate = res.data[0];
      }
    });
    //查询全部图书
    uni.request({
      url: `${Host}/book/list`,
      success: res => {
        this.books = res.data;
      }
    });
  },
  methods: {
    changeCate(cate) {
	  this.currentCate = cate;
	  const url = Number(cate.no)==0?`${Host}/book/list`:`${Host}/book/cate`;
      //查询指定分类下的books
      uni.request({
        url,
        data:{cate: cate.no},
        success: res => {
          this.books = res.data;
        }
      });
	},
	//根据指定关键字搜书
	//TODO：根据书名、译名、作者名模糊查询
	queryBook(keyword){
		uni.request({
			url:`${Host}/books/query`,
			data:{keyword},
			success: res => {
				this.books = res.data;
			}
		});
	},
	//跳转到book详情页
	navToDetail(book){
		uni.navigateTo({
			url:`./detail?id=${book._id}`
		});
	}
  }
};
</script>

<style>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.row {
  display: flex;
  flex-direction: row;
}
.column {
  display: flex;
  flex-direction: column;
}

</style>
