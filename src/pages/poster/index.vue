<template>
  <div class="container ub-box ub-col ub-ver">

    <img src="http://goldsys.oss-cn-hangzhou.aliyuncs.com/1553045175167.jpg" alt="" class="topImg">
    <div class="btnStyle" @click.stop="formSubmit()">生成海报</div>

    <!--海报-->
    <div class="imagePathBox" v-show="maskHidden">

      <img :src="imagePath" alt="" class='shengcheng'>

      <button class='baocun' @click.stop="baocun()">保存相册，分享到朋友圈</button>

    </div>
    <div class="mask" v-show="maskHidden"></div>

    <div class="canvas-box">

      <canvas  style="width: 375px;height: 667px;position:fixed;top:9999px" canvas-id="mycanvas"/>

    </div>

  </div>

</template>

<script>
    export default {
        name: "index",
      data(){
          return{
            imagePath:'',
            maskHidden:false,
            img: "http://goldsys.oss-cn-hangzhou.aliyuncs.com/1553045175167.jpg",   //背景图
            cardCode: "http://goldsys.oss-cn-hangzhou.aliyuncs.com/1553154132191.jpg",   //二维码
          }
      },
      created:function () {

      },
      onShow(){
        wx.setNavigationBarTitle({title: '宣传海报'})
      },
      methods:{
        // getPosterBtn(){
        //   console.log('点击生成');
        //   this.$data.maskHidden = true;
        // },
        //将canvas转换为图片保存到本地，然后将图片路径传给image图片的src
        createNewImg: function () {
          console.log('canvas')
          var that = this;
          var context = wx.createCanvasContext('mycanvas');
          context.setFillStyle("#ffffff")   //填充整体的色调#697fde  ffe200
          // 设置上部的图片 /images/gobg.png
          context.fillRect(0, 0, 375, 667)
          var path = that.$data.img;
          var path1 = that.$data.cardCode;
          //将模板图片绘制到canvas,在开发工具中drawImage()函数有问题，不显示图片
          //不知道是什么原因，手机环境能正常显示   //绘制二维码touxiang
          context.drawImage(path, 48, 20, 280, 460);

          context.drawImage(path1, 136, 520, 100, 100);



          //绘制领券标语
          context.setFontSize(17);
          context.setFillStyle('#333333');
          context.setTextAlign('center');
          context.fillText("程繁繁邀请您领券，一起选珠宝", 185, 510);
          context.stroke();


          //绘制领码提醒
          context.setFontSize(14);
          context.setFillStyle('#333333');
          context.setTextAlign('center');
          context.fillText('长按识别二维码', 185, 650);
          context.stroke();


          context.draw();
          //将生成好的图片保存到本地，需要延迟一会，绘制期间耗时
          setTimeout(function () {
            wx.canvasToTempFilePath({
              canvasId: 'mycanvas',
              success: function (res) {
                var tempFilePath = res.tempFilePath;

                console.log(tempFilePath)
                that.$data.imagePath = tempFilePath;
                that.$data.canvasHidden = true;
              },
              fail: function (res) {
                console.log(res);
              }
            });
          }, 200);
        },
        //点击保存到相册
        baocun: function () {
          var that = this
          wx.saveImageToPhotosAlbum({
            filePath: that.$data.imagePath,
            success(res) {
              wx.showModal({
                content: '图片已保存到相册，赶紧晒一下吧~',
                showCancel: false,
                confirmText: '好的',
                confirmColor: '#333',
                success: function (res) {
                  if (res.confirm) {
                    console.log('用户点击确定');
                    /* 该隐藏的隐藏 */
                    that.$data.maskHidden = false;
                  }
                }, fail: function (res) {
                  console.log(11111)
                }
              })
            }
          })
        },
        //点击生成
        formSubmit: function (e) {
          var that = this;
          that.$data.maskHidden = false;
          wx.showToast({
            title: '生成中...',
            icon: 'loading',
            duration: 1000
          });
          setTimeout(function () {
            wx.hideToast()
            that.createNewImg();
            wx.vibrateLong();
            that.$data.maskHidden = true;

          }, 1000)
        },





      },
    }
</script>

<style scoped>
  .topImg{
    width: 300px;
    height: 460px;
    margin: 0 auto;
    margin-top: 10px;
    /*border:1px solid salmon;*/
  }
  .btnStyle{
    width: 90px;
    height: 40px;
    line-height: 40px;
    font-size: 16px;
    text-align: center;
    background-color: #11b8ae;
    border-radius: 5px;
    margin-top: 30px;
  }
  .imagePathBox{
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.7);
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 10;
  }
  .shengcheng{
    width: 80%;
    height: 80%;
    position: fixed;
    top: 50rpx;
    left: 50%;
    margin-left: -40%;
    z-index: 10;
  }
  .baocun{
    display: block;
    width: 418rpx;
    height: 78rpx;
    border-radius: 6.94rpx;
    border: solid 2px #647adb;
    padding: 0;
    margin: 0 auto;
    line-height: 78rpx;
    text-align: center;
    position: fixed;
    bottom: 50rpx;
    left: 23%;
    background-color: #ffffff;
    color: #647adb;
    font-size: 29.16rpx;
  }
</style>
