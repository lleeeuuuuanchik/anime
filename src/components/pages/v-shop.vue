<template>
  <div class="body">
    <div class="shop-container">
        <header>
            <img @click="showPerfomance(0)"  src="@/assets/img/logo_black.png" alt="">
            <nav>
                <a>Toys</a>
                <a @click="showPerfomance(2)" >Tarrifs</a>
                <a @click="showPerfomance(3)" >About us</a>
            </nav>
            <div class="for-change-card-lenght">
                <img  @click="switchCardLenghtPlus"  src="@/assets/img/1.png" alt="">
                <img  @click="switchCardLenghtMinus" src="@/assets/img/2.png" alt="">
                <img  @click="showPerfomance(4)"  src="@/assets/img/cart.png" alt="">
            </div>
        </header>

        <body>
            <form action="">
                <input v-model="NapisanoAAA" type="text" placeholder="write here...">
                <div class = "productsSearch">
                    <p class = "productList" v-for="(item, index) in searchAnyToy" :key="index">
                        {{item.name}}
                    </p>
                </div>
            </form>
        </body>

        <div class="cardContainer">
            <vCard @addToCart="addToCart" v-for="(item, index) in cardArray" :key="index" :item = "item" v-show="maxIndex >= index && minIndex <= index"> </vCard>
        </div>

        <div class="paggination-container">
            <div class="paggination">
                <span :class="{'active':currentSlide === index}" @click="nextSlide(index)" v-for="(item, index) in Math.ceil(cardArray.length/countSlide)" :key="index">{{index+1}}</span>
            </div>
        </div>
        
    </div>
    <footer >
        <div class="footer-container">
            <p>contact: +7 (963) 179-88-77</p>
            <img src="@/assets/img/logo_white.png" alt="">
            <p>Email: levanlazarov20@gmail.com</p>
        </div>
    </footer>
  </div>
</template>

<script>
import vCard from "@/components/card.vue"
export default {
    data() {
        return {
            cardArray: [
                {id: 1, img: "product-1-removebg-preview.png", name: "Naruto Uzumaki", information: "The most popular anime character", price: "500$",},
                {id: 2, img: "product-2-removebg-preview.png", name: "Levi", information: "The most popular anime character", price: "500$",}, 
                {id: 3, img: "product-3-removebg-preview.png", name: "Sergei", information: "The most popular anime character", price: "500$",},
                {id: 4, img: "product-4-removebg-preview.png", name: "Zaur", information: "The most popular anime character", price: "500$",},
                {id: 5, img: "product-4-removebg-preview.png", name: "Levan", information: "The most popular anime character", price: "500$",},
                
            ],

            cartArray: [],

            currentSlide: 0,

            maxIndex: 2,
            minIndex: 0,
            min: 0,
            max: 2,
            countSlide: 3,

            NapisanoAAA: ""
        }
    },

    computed: {
        searchAnyToy() {
            if(this.NapisanoAAA.length === 0) {
                return
            }
            else {
                return this.cardArray.filter( item => {
                    return item.name.toLowerCase().includes(this.NapisanoAAA)
                })
            }
        }
    },

    methods: {
        showPerfomance(number) {
            console.log(number)
            this.$emit("perfomanceShow", number)
            
        },

        nextSlide(index) {
            this.minIndex = this.min+(this.countSlide*index)
            this.maxIndex = this.max+(this.countSlide*index)

            this.currentSlide = index
            
        },

        addToCart(item) {
            console.log("Вывод индекса ", this.cardArray[this.cardArray.indexOf(item)] );
            this.$emit("addToCart", this.cardArray[this.cardArray.indexOf(item)])
            
            this.$swal('Товар добавлен в корзину')
        },

        switchCardLenghtPlus() {
            this.countSlide = 3
            this.max = 2
            this.maxIndex = 2
            
        },

        switchCardLenghtMinus() {
            this.countSlide = 2
            this.max = 1
            this.maxIndex = 1
            
        },

      
    },

    components: {
        vCard,
    },

    props: {
        
    }
}



</script>

<style scoped>
    .body {
        width: 100vw;
        height: 100vh;
        display: flex;
        justify-content: center;
        background: linear-gradient(180deg, #B1F0FF 0%, rgba(217, 248, 255, 0) 100%);
    }

    .shop-container {
        width: 1400px;
        height: 100vh;
    }
    .footer-container {
        width: 1400px;
        height: 150px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    header {
        height: 60px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    header img {
        cursor: pointer;
    }

    nav {
        display: flex;
        gap: 40px;
    }

    nav a {
        text-decoration: none;
        font-family: 'Montserrat', sans-serif;
        font-style: normal;
        font-weight: 600;
        font-size: 18px;
        line-height: 22px;
        /* identical to box height */
        color: #000000;
    }

    .for-change-card-lenght {
        display: flex;
        gap: 20px;
    }

    .for-change-card-lenght img {
        width: 30px;
        height: 30px;
    }

    /* body */

    input {
        padding: 14px 30px;
        font-family: 'Montserrat', sans-serif;
        font-style: normal;
        font-weight: 400;
        font-size: 18px;

        width: 1200px;
        height: 50px;
        background: transparent;
        outline: none;
        border: 2px solid #000000;
        border-radius: 10px;

        transition: 0.1s ease;

        background-image: url('lupa.png');
      
        background-position: 98%;
       
        background-repeat: no-repeat;

    }

    form {
        width: 100%;
        display: flex;
        justify-content: center;
        margin-top: 50px;
        
    }

    .productsSearch {
        position: absolute;
        font-size: 20px;
        top: 18%;
        width: 1200px;
        color: white;
        background: rgba(0, 0, 0, 0.5);
        border-radius: 10px;
    }

    .productsSearch p {
        margin: 20px;

    }

    input:focus {
        border: 3px solid #1b5557;
        box-shadow: 0 0 3px #1b5557;
    }

    input::placeholder {
        font-family: 'Montserrat', sans-serif;
        font-style: normal;
        font-weight: 400;
        font-size: 18px;
        /* identical to box height */


        color: #7B7B7B;
    }


    .cardContainer {
        display: flex;
        justify-content: center;
        gap: 100px;
        margin-top: 25px;
        width: 100%;
        padding: 0px 100px;
    }

    .paggination-container {
        width: 100%;
        display: flex;
        justify-content: center;
        margin-top: 15px ;
    }

    .paggination {
        display: flex;
        gap: 20px;
        
        
    }

    .paggination span {
        padding: 14px 21px;
        border-radius: 5px;
        background: transparent;
        color: rgb(0, 0, 0);
        display: block;
        width: max-content;
        font-family: 'Montserrat';
        font-style: normal;
        font-weight: 800;
        font-size: 18px;
        line-height: 22px;
        /* identical to box height */
        height: max-content;
        cursor: pointer;
    }

    .paggination span.active {
        background: #FF9900;
    }

    /* footer */

    footer {
        width: 100vw;
        height: 150px;
        background-color: #000000;
        position: absolute;
        bottom: 0;
        display: flex;
        justify-content: center;
    }

    .footer-container > p {
        font-family: 'Montserrat', sans-serif;
        font-style: normal;
        font-weight: 500;
        font-size: 18px;
        line-height: 22px;
        /* identical to box height */
        color: #FFFFFF;
    }
</style>