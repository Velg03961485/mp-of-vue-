<template>
  <div class="container ub-box ub-col ub-ver">
    <!--顶部搜索-->
    <div class="top">
      <img src="/static/images/3-3.png" alt="" class="topOne">
      <div class="topTow">
        <img src="/static/images/search.png" alt="" class="topTow_a">
        <input type="text" class="topTow_b" placeholder="请搜索美食">
      </div>
      <img src="/static/images/a-6.png" alt="" class="topThree">
    </div>

    <!--瀑布流展示图片-->
    <div class="pullList">

      <div class="img_item">
        <div class="pullItem" v-for="(item, idx) in imgData" :key="idx">
          <img :src="item.url" alt="" class="pullItemOne">
          <div class="pullItemTow">特色沙拉饭</div>
          <div class="pullItemThree">
            <img src="/static/images/star_2.png" alt="" class="pullItemThree_a">
            <div class="pullItemThree_b">{{item.num}}K</div>
            <img src="/static/images/2-5.png" alt="" class="pullItemThree_c">
            <div class="pullItemThree_d">{{item.numB}}}</div>
          </div>
        </div>
      </div>

      <div class="img_item">
        <div class="pullItem" v-for="(item, idx) in imgData2" :key="idx">
          <img :src="item.url" alt="" class="pullItemOne">
          <div class="pullItemTow">特色沙拉饭</div>
          <div class="pullItemThree">
            <img src="/static/images/star_2.png" alt="" class="pullItemThree_a">
            <div class="pullItemThree_b">{{item.num}}K</div>
            <img src="/static/images/2-5.png" alt="" class="pullItemThree_c">
            <div class="pullItemThree_d">{{item.numB}}}</div>
          </div>
        </div>
      </div>




    </div>

    <!--<view style="display:none">-->
      <!--<image v-for="images" :key="id" :id="item.id" :src="item.url" bindload="onImageLoad"></image>-->
    <!--</view>-->
    <!--<div style="display:none">-->
      <!--<img :src="item.url" v-for="images" :key="id" :id="item.id" :src="item.url" alt="" >-->
    <!--</div>-->

  </div>
</template>

<script>
  let col1H = 0;
  let col2H = 0;
    export default {
        name: "index",
      data(){
          return{
            imgData:[
              {url:'/static/images/1 (1).jpg',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (1).png',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (2).jpg',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (2).png',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (3).png',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (4).jpg',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (4).png',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (5).jpg',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (5).png',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (6).jpg',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (6).png',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (7).jpg',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (7).png',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (8).jpg',num:12,numB:130, height: 0 },

            ],
            imgData2:[
              {url:'/static/images/1 (8).jpg',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (8).png',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (9).jpg',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (9).png',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (5).png',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (6).jpg',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (6).png',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (1).jpg',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (1).png',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (2).jpg',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (2).png',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (8).png',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (9).jpg',num:12,numB:130, height: 0 },
              {url:'/static/images/1 (9).png',num:12,numB:130, height: 0 },
            ],

          }
      },
      created:function () {


      },
      onShow(){
        wx.setNavigationBarTitle({title: '杭州美食节'})
      },
      methods:{

      },

    }
</script>

<style scoped>

  .top{
    width: 100%;
    height: 60rpx;
    /*border:1px solid salmon;*/
    display: flex;
    flex-direction: row;
    /*background-color: #999999;*/
    background-color: #fff;
    /*opacity: 0.6;*/
    margin-top: 18rpx;
  }
  .topOne{
    width: 30rpx;
    height: 40rpx;
    /*border:1px solid seagreen;*/
    margin-top: 10rpx;
    margin-left: 30rpx;
  }
  .topTow{
    width: 580rpx;
    height: 50rpx;
    /*border:1px solid sandybrown;*/
    display: flex;
    flex-direction: row;
    margin-top: 5rpx;
    margin-left: 30rpx;
    border-left: 2px solid #999999;
  }
  .topTow_a{
    width: 40rpx;
    height: 40rpx;
    /*border:1px solid seagreen;*/
    margin-top: 5rpx;
    margin-left: 20rpx;

  }
  .topTow_b{
    width: 485rpx;
    height: 50rpx;
    margin-left: 10rpx;
    font-size: 23rpx;
    padding-left: 5rpx;
  }
  .topThree{
    width: 36rpx;
    height: 40rpx;
    /*border:1px solid seagreen;*/
    margin-top: 10rpx;
    margin-left: 10rpx;
  }

  .pullList{
    width: 100%;
    height: 1098rpx;
    /*border:1px solid seagreen;*/
    margin-top: 20rpx;
    overflow-y: scroll;
    /*display: flex;*/
    /*flex-direction: row;*/

  }
  .img_item{
    display: inline-block;
    vertical-align: top;
    width: 50%;
  }
  .pullItem{
    width: 300rpx;
    /*height: 100%;*/
    /*border:1px solid seagreen;*/
    display: flex;
    flex-direction: column;
    margin: 0 auto;
    margin-top: 10rpx;
    /*margin-left: 20rpx;*/
    background-color: #ffffff;
    box-shadow: 0rpx -3rpx 12.6rpx 1.4rpx
    rgba(60, 60, 60, 0.1);
    border-radius: 8rpx;

  }
  .pullItemOne{
    width: 300rpx;
    /*height: 100%;*/
    border-radius: 8rpx;
    margin: 0 auto;
  }
  .pullItemTow{
    width: 260rpx;
    height: 50rpx;
    font-size: 27rpx;
    line-height: 50rpx;
    border-bottom: 1rpx solid #000;
    margin: 0 auto;
    margin-top: 10rpx;
  }
  .pullItemThree{
    width: 260rpx;
    height: 30rpx;
    /*border:1px solid sandybrown;*/
    display: flex;
    flex-direction: row;
    margin: 0 auto;
    margin-top: 20rpx;
    margin-bottom: 10rpx;
  }
  .pullItemThree_a{
    width: 28rpx;
    height: 28rpx;
  }
  .pullItemThree_b{
    width: 80rpx;
    height: 30rpx;
    font-size: 26rpx;
    line-height: 30rpx;
    margin-left: 10rpx;
  }
  .pullItemThree_c{
    width: 28rpx;
    height: 28rpx;
  }
  .pullItemThree_d{
    width: 80rpx;
    height: 30rpx;
    font-size: 26rpx;
    line-height: 30rpx;
    margin-left: 10rpx;
  }
</style>
