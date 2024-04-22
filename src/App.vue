<script setup lang="ts">
  import { ref, onMounted } from "vue"
  import { Swiper, SwiperSlide } from "swiper/vue";
  import "swiper/css/pagination";
  import "swiper/css";
  import { Navigation, Pagination, Scrollbar, A11y } from 'swiper/modules';
  
  onMounted(() => {
    const swp: any = document.querySelector('.swiper');
    console.log(swp)
    const currentSlide: any = swp.slides[0]
      let video =  currentSlide.querySelector('video')
      if(video.height > video.width){
        video.classList.remove('vid')
        video.classList.add('normalized')
      } else {
        video.classList.remove('normalized')
        video.classList.add('vid')
      }
})
  const modules = [ Navigation, Pagination, Scrollbar, A11y ]
  let play = ref(true)
  const onSlideClick =  (e: any) => {
    console.log(play.value)
    if(play.value == true){
      const currentSlide: any = e.slides[e.activeIndex]
      let video =  currentSlide.querySelector('video')
      if(video.height > video.width){
        video.classList.remove('vid')
        video.classList.add('normalized')
      } else {
        video.classList.remove('normalized')
        video.classList.add('vid')
      }
      video.play()

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
      let video = currentSlide.querySelector('video')
      if(video.height > video.width){
        video.classList.remove('vid')
        video.classList.add('normalized')
      } else{
        video.classList.remove('normalized')
        video.classList.add('vid')
      }
      video.currentTime = 0
      video.play()
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
        <img v-if="play" src="./assets/svg/play.svg" class="pause">
        <video class="vid" loop> 
          <source src="/video/1.mp4" type='video/mp4' />
        </video>
      </swiper-slide>
      <swiper-slide>
        <img v-if="play" src="./assets/svg/play.svg" class="pause">
        <video class="vid" loop>
          <source src="/video/2.mp4" type='video/mp4' />
        </video>
      </swiper-slide>
      <swiper-slide>
        <img v-if="play" src="./assets/svg/play.svg" class="pause">
        <video class="vid" loop>
          <source src="/video/3.mp4" type='video/mp4' />
        </video>
      </swiper-slide>
    </swiper>
  </div>
</div>
</template>

