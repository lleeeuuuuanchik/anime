<template>
  <div class="card-container">
      
      <img class = "img" :src="require(`../assets/img/for_card/${item.img}`)" alt="">
      <h2>{{item.name}}</h2>
      <p class="card-information">{{item.information}}</p>
      <p class="card-price">{{item.price}}</p>
      <button class="card-button">add to card</button>
  </div>
</template>

<script>
export default {
    data() {
        return {

        }
    },

    props: {
        item: {
            type: Object
        }
    }
}
</script>

<style scoped>
    .card-container {
        width: 300px;
        height: auto;
            
        flex-direction: column;
    }

    .card-container * {
        margin-bottom: 10px;
    }

    .img {
        width: 300px;
        height: 300px;
    }

    h2 {
        font-family: 'Montserrat', sans-serif;
        font-style: normal;
        font-weight: 700;
        font-size: 24px;
        line-height: 29px;

        color: #000000;
    }

    .card-information {
        font-family: 'Montserrat', sans-serif;
        font-style: normal;
        font-weight: 500;
        font-size: 18px;
        line-height: 22px;
        /* identical to box height */


        color: #000000;
    }

    .card-price {
        font-family: 'Montserrat', sans-serif;
        font-style: normal;
        font-weight: 700;
        font-size: 24px;
        line-height: 29px;

        color: #FF0000;
    }

    .card-button {
        width: 300px;
        height: 50px;
        background: #FF9900;
        backdrop-filter: blur(5px);
        /* Note: backdrop-filter has minimal browser support */

        border-radius: 10px;

        font-family: 'Montserrat', sans-serif;
        font-style: normal;
        font-weight: 800;
        font-size: 18px;
        line-height: 22px;
        /* identical to box height */


        color: #FFFFFF;
    }
    
</style>