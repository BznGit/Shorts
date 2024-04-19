<script setup lang="ts">
  import { Swiper, SwiperSlide } from "swiper/vue";
  import "swiper/css/pagination";
  import "swiper/css";
  import { Navigation, Pagination, Scrollbar, A11y } from 'swiper/modules';
  
  const modules = [ Navigation, Pagination, Scrollbar, A11y ]
  const onSwiper = (swiper: any) => {
   console.log(swiper.el.querySelector('video').play())
    swiper.el.querySelector('video').play()
      };
  const onSlideChange = (e: any) => {

    const currentSlide: any = e.slides[e.activeIndex]
    currentSlide.querySelector('video').play()
  };
  const onSlideClick =  (e: any) => {
    console.log(e,'clik')
  }

</script>

<template>
<div class="swiper">
  <!-- Additional required wrapper -->
  <div class="swiper-wrapper">
    <swiper
      :slides-per-view="1"
      :space-between="10"
      :modules="modules"
      :direction="'vertical'"
      @swiper="onSwiper"
      @slideChange="onSlideChange"
      @click="onSlideClick"
    >
      <swiper-slide   >
        <video 
        >
        <source src="/video/1.mp4" type='video/mp4' />
      </video>
      </swiper-slide>
      <swiper-slide >
        <video 

        >
        <source src="/video/2.mp4" type='video/mp4' />
      </video>
      </swiper-slide>

      <swiper-slide >
        <video 
        >
        <source src="/video/3.mp4" type='video/mp4' />
      </video>
      </swiper-slide>
      
    </swiper>
  </div>
</div>
</template>

