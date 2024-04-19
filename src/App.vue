<script setup lang="ts">
  import { Swiper, SwiperSlide } from "swiper/vue";
  import "swiper/css/pagination";
  import "swiper/css";
  import { Navigation, Pagination, Scrollbar, A11y } from 'swiper/modules';
  
  const modules = [ Navigation, Pagination, Scrollbar, A11y ]
  const onSwiper = (swiper: Object) => {
        console.log(swiper);
      };
  const onSlideChange = () => {
    console.log('slide change');
  };
</script>

<template>
<div class="swiper">
  <!-- Additional required wrapper -->
  <div class="swiper-wrapper">
    <swiper
      :slides-per-view="1"
      :space-between="10"
      :modules="modules"
      navigation
      :pagination="{ clickable: true }"
      :scrollbar="{ draggable: true }"
      @swiper="onSwiper"
      @slideChange="onSlideChange"
    >
      <swiper-slide>Slide 1</swiper-slide>
      <swiper-slide>Slide 2</swiper-slide>
      <swiper-slide>Slide 3</swiper-slide>
      
    </swiper>
  </div>
  <!-- If we need pagination -->
  <div class="swiper-pagination"></div>

  <!-- If we need navigation buttons -->
  <div class="swiper-button-prev"></div>
  <div class="swiper-button-next"></div>

  <!-- If we need scrollbar -->
  <div class="swiper-scrollbar"></div>
</div>
</template>

<style scoped>

</style>
