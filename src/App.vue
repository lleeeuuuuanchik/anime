

// ------------------------------------------------------ HTML

<template>
  <div class = "slider">
    <carousel :items-to-show="1" :autoplay="10000" :transition="1500" :wrap-around="true" :touchDrag="false" :mouseDrag="false">
      <slide v-for="(slide, index) in arraySlider" :key="index">
        <img :src="require(`./assets/img/for_slide/${slide.img}`)" class="slider__img" alt="">
      </slide>
    </carousel>
    <div class="slider__header">
      <img src="./assets/img/logo_white.png" class="header__logo" alt="">
    </div>
  </div>
  
</template>_


// ------------------------------------------------------ JS

<script>
import database from "./array.js"
import 'vue3-carousel/dist/carousel.css';
import { Carousel, Slide } from 'vue3-carousel';
export default {
  data() {
    return {
      arraySlider: []
    }
  },

  components: {
    Carousel,
    Slide,
  },

  created() {
    this.arraySlider = database.sliderImg()
  }
}
</script>


// ------------------------------------------------------ CSS

<style src="./assets/perfomance.css" >

</style>
