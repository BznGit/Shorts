<script setup lang="ts">
  import { ref } from "vue"
  import { Swiper, SwiperSlide } from "swiper/vue";
  import "swiper/css/pagination";
  import "swiper/css";
  import { Navigation, Pagination, Scrollbar, A11y } from 'swiper/modules';
  
  const modules = [ Navigation, Pagination, Scrollbar, A11y ]
  let play = ref(false)
  const onSlideClick =  (e: any) => {
    if(play.value == true){
      const currentSlide: any = e.slides[e.activeIndex]
      currentSlide.querySelector('video').play()
      play.value = false
    }else{
      const currentSlide: any = e.slides[e.activeIndex]
      currentSlide.querySelector('video').pause()
      play.value = true
    }
  }
  const onSlideChange = (e: any) => {
    if(!play.value){
      e.slides.forEach((item: any) => item.querySelector('video').pause())
      const currentSlide: any = e.slides[e.activeIndex]
      currentSlide.querySelector('video').play()
    }else return

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
      :direction="'vertical'"
      @slideChange="onSlideChange"
      @click="onSlideClick"
    >  
      <swiper-slide>
        <div v-if="play"  class="stop">stop</div>
        <video>
          <source src="/video/1.mp4" type='video/mp4' />
        </video>
      </swiper-slide>
      <swiper-slide>
        <div v-if="play" class="stop">stop</div>
        <video>
          <source src="/video/2.mp4" type='video/mp4' />
        </video>
      </swiper-slide>
      <swiper-slide>
        <div v-if="play" class="stop">stop</div>
        <video>
          <source src="/video/3.mp4" type='video/mp4' />
        </video>
      </swiper-slide>
    </swiper>
  </div>
</div>
</template>

