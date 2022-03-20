

// ------------------------------------------------------ HTML

<template>
  <div class="perfomance" v-show="switchPage === 0">
    <div class = "slider">
      <vCarousel :arraySlider="arraySlider"></vCarousel>
    </div>
    <div class="slider__header">
      <img src="./assets/img/logo_white.png" class="header__logo" alt="">
    </div>
    <div class="center">
      <div class="center-cont">
        <div class="information-and-button">
          <p class = "slogan">You can find <br> any toys here</p>
          <button @click="switchPage = 1">Find</button>
        </div>
      </div>
    </div>
  </div>

  <vShop v-show="switchPage === 1" @perfomanceShow = "returnToPerfomance"></vShop>
  
  <vAbout v-show="switchPage === 2" @perfomanceShow = "returnToPerfomance"></vAbout>
  <vTarrifs v-show="switchPage === 3" @perfomanceShow = "returnToPerfomance"></vTarrifs>


</template>


// ------------------------------------------------------ JS

<script>
import database from "./array.js"
import vCarousel from "./components/v-carousel.vue"
import vShop from "./components/pages/v-shop.vue"
import vAbout from "./components/pages/v-shop.vue"
import vTarrifs from "./components/pages/v-shop.vue"


export default {
  data() {
    return {
      arraySlider: [],
      show: true,
      switchPage: 0,
    }
  },

  components: {
    vCarousel,
    vShop,
    vAbout,
    vTarrifs,
  },

  methods: {

    returnToPerfomance(numberPages) {
      this.switchPage = numberPages
      console.log(numberPages)
      console.log(this.switchPage)
      
    }

  },

  created() {
    this.arraySlider = database.sliderImg()
  }
}
</script>


// ------------------------------------------------------ CSS

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,500;0,800;1,600;1,700&display=swap');
/* font-family: 'Montserrat', sans-serif; */
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

/* slogan */

  .center {
    display: flex;
    justify-content: center;
  }

  .center-cont {
    width: 1400px;
    height: 80vh;
    display: flex;
    align-items: center;
  }

  .slogan {
    font-family: 'Montserrat', sans-serif;
    font-style: normal;
    font-weight: 700;
    font-size: 64px;
    color: white;
    line-height: 88px;
    margin-bottom: 30px;
    text-decoration: none;
  }

  button {
    font-family: 'Montserrat', sans-serif;
    font-style: normal;
    font-weight: 600;
    color: white;
    font-size: 36px;
    line-height: 44px;
    width: 327px;
    height: 74px;
    background: linear-gradient(93.53deg, rgba(78, 212, 255, 0.25) 2.74%, rgba(75, 212, 255, 0.05) 100%);
    backdrop-filter: blur(5px);
    /* Note: backdrop-filter has minimal browser support */
    border-radius: 10px;
    cursor: pointer;
    border:none;
  }

  button:hover {
    background: linear-gradient(93.53deg, rgba(78, 212, 255, 0.70) 2.74%, rgba(75, 212, 255, 0.1) 100%)
  }


</style>