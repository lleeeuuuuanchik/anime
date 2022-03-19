

// ------------------------------------------------------ HTML

<template>

  <div class = "slider">
    <vCarousel :arraySlider="arraySlider"></vCarousel>
  </div>

  <div class="slider__header">
    <img src="./assets/img/logo_white.png" class="header__logo" alt="">
  </div>
  
</template>


// ------------------------------------------------------ JS

<script>
import database from "./array.js"
import vCarousel from "./components/v-carousel.vue"

export default {
  data() {
    return {
      arraySlider: []
    }
  },

  components: {
    vCarousel
  },

  created() {
    this.arraySlider = database.sliderImg()
  }
}
</script>


// ------------------------------------------------------ CSS

<style>

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.slider {
  width: 100vw;
  height: 100vh;
  /* overflow: hidden; */
  position: absolute;
  z-index: -1;
}



/* logo */
.slider__header {
  width: 100vw;
  height: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  /* position: absolute; */
  z-index: 1000;
}
</style>