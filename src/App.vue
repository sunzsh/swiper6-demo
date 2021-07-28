<template>
<button @click="changeBg">点击将第一个设置背景颜色</button>
<swiper :pagination="true" loop="true" class="mySwiper">
  <swiper-slide :class="{'bg': item.bg}" v-for="item in datas" :key="item.text">{{item.text}}</swiper-slide>
  </swiper>
</template>
<script>
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue';

// Import Swiper styles
import 'swiper/swiper.scss';
import 'swiper/swiper-bundle.css'
import "swiper/components/pagination/pagination.min.css"
import './style.css';


// import Swiper core and required modules
import SwiperCore, { Pagination } from 'swiper/core';

// install Swiper modules
SwiperCore.use([Pagination]);


export default {
  components: {
    Swiper,
    SwiperSlide
  },
  data() {
    return {
        datas: [
          { text: 'Slide 1', bg: false },
          { text: 'Slide 2', bg: false },
          { text: 'Slide 3', bg: false },
          { text: 'Slide 4', bg: false }
        ]
        
    };
  },
  methods: {
    changeBg() {
      this.datas[0].text = "abaababab";
      this.datas[0].bg = true;
    }
  }
  
}
</script>
<style scoped>
/* 这里需要添加一个带有样式穿的选择器（::v-deep .xxx ） 用来命中被组件复制的item */
.bg, ::v-deep .bg {
  background-color: red;
}
</style>