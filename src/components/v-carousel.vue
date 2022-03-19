<template>
  
  <carousel class="container" :items-to-show="1" :autoplay="10000" :transition="1500" :wrap-around="true" :touchDrag="false" :mouseDrag="false">
    <slide class="carousel__viewport" v-for="(slide, index) in arraySlider" :key="index">
      <div class="one"></div>
      <img :src="require(`../assets/img/for_slide/${slide.img}`)" class="slider__img" alt="">
    </slide>
  </carousel>

</template>

<script>
import 'vue3-carousel/dist/carousel.css';
import { Carousel, Slide } from 'vue3-carousel';

export default {
  data(){
    return{
      
    }
  },

  components:{
    Carousel,
    Slide
  },

  props:{
    arraySlider:{
      type: Array
    }
  }
}
</script>

<style scoped>

.container {
  width: 100vw;
  height: 100vh;
  position: relative;
}

.carousel__viewport{
  width: 100vw; height: 100vh;
  position: relative;
}

.slider__img {
  width: 100%;
  height: 100%;
  /* position: absolute; */
  object-fit: cover;
  -o-object-fit: cover;
  object-position: center center;  
}

/* stars */
.one{
  position: absolute;
  left: 10px;
  top: 10px;
  opacity: 75%;
  width: 5px; height: 5px;
  border-radius: 50%;
  background: white;
  box-shadow: 0 0 10px white;
  animation: dropColor 2s linear infinite;
}

@keyframes dropColor{
  75%{
    opacity: 35%;
  }
}
</style>