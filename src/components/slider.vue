<template>
  <div class="home-swiper">
        <div class="swiper-container home-swiper-box" @mouseenter="stopPlay" @mouseleave="startPlay">
            <div class="swiper-wrapper">
                <div class="swiper-slide" v-for="(slide,index) in bannerList" :key="index">
                    <img :src="slide.url">
                    <p>第{{index+1}}张图片</p>
                </div>
            </div>

            <div class="swiper-pagination"></div>
            <!-- <div class="swiper-button-prev"></div>
            <div class="swiper-button-next"></div> -->
        </div>
    </div>
</template>

<script>
import "swiper/dist/css/swiper.css";
import Swiper from "swiper";
export default {
  name: "slider",
  data() {
    return {
      bannerList: [{
        url:'http://img1.qunarzz.com/piao/fusion/1805/ab/0364cd7b56f95702.jpg_750x200_ccb27048.jpg'
      },{
        url:'http://img1.qunarzz.com/piao/fusion/1804/a8/31be8a58c2556302.jpg_750x200_0dda540c.jpg'
      },{
        url:'http://img1.qunarzz.com/piao/fusion/1805/5f/c08ce08779ff8202.jpg_750x200_3a907189.jpg'
      },{
        url:'http://img1.qunarzz.com/piao/fusion/1804/f2/91b285a08ee21c02.jpg_750x200_8a73fd08.jpg'
      },{
        url:'http://img1.qunarzz.com/piao/fusion/1804/3e/4d6e12949f74fc02.jpg_750x200_22aba1bb.jpg'
      }],
      number: ""
    };
  },
  components: {},
  created: function() {
    // this.getBanner();
  },
  mounted: function() {
    let that = this;
    that.$nextTick(function() {
      setTimeout(function() {
        let initialSlide = Math.floor(that.number / 2);
        that.mySwiper = new Swiper(".swiper-container", {
          loop: true,
          loopedSlides: "2",
          autoplay: {
            delay: 3000
          },
          pagination: {
            el: ".swiper-pagination",
            clickable: true
          },
          effect: "coverflow",
          slidesPerView: 1.13,
          centeredSlides: true,
          coverflowEffect: {
            rotate: 0,
            stretch: -16,
            depth: 70,
            modifier: 2,
            slideShadows: false
          }
          // navigation: {
          //   nextEl: '.swiper-button-next',
          //   prevEl: '.swiper-button-prev',
          // },
        });
        // 初始化swiper显示为中间数
        that.mySwiper.slideToLoop(initialSlide, 1000, false);
      }, 200);
    });
  },
  methods: {
    stopPlay: function() {
      console.log("轮播停止");
    },
    startPlay: function() {
      console.log("轮播启动");
    },
    getBanner: function() {
      // this.axios.get("/api/homebanner").then(res => {
      //   // console.log(res);
      //   this.bannerList = res.data.imgUrl;
      //   this.number = res.data.imgUrl.length;
      }
    }
  }

</script>

<style lang="less" scoped>
.home-swiper-box {
  padding-top: 6px;
  padding-bottom: 34px;
  max-width: 650px;
}
.home-swiper-box .swiper-slide {
  opacity: 0.5;
  transition: 0.3s ease-in-out;
  position: relative;
}
.home-swiper-box .swiper-slide p {
  position: absolute;
  bottom: 20px;
  left: 0;
  right: 0;
  margin: auto;
  text-align: center;
  font-size: 20px;
  color: #fff;
}
.home-swiper-box .swiper-slide-active {
  opacity: 1;
}
.home-swiper-box {
  overflow: visible;
}
.home-swiper-box .swiper-slide-active img {
  box-shadow: 0 0 15px #d6d9e6;
}
.home-swiper-box .swiper-slide img {
  width: 100%;
  border-radius: 10px;
}
.home-swiper-box .swiper-pagination .swiper-pagination-bullet {
  width: 10px;
  height: 10px;
  border-radius: 10px;
  opacity: 1;
  background-color: #ebedf4;
  transition: 0.3s ease-in-out;
}
.home-swiper-box .swiper-pagination .swiper-pagination-bullet-active {
  width: 24px;
  background-color: #ffdc00;
}
</style>

