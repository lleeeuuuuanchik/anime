<template>
  <div class="switcher product__switcher">
        <button  @click="val--" class="switcher__btn switcher__btn--plus">-</button>
        <input class="switcher__value" :value="val">
        <button @click="val++" class="switcher__btn switcher__btn--minus">+</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            val: 1
        }
    },

    watch: {
        val(newVal) {
            if (newVal < 1) {
                this.val = 1
                
            }
        }
    }
}
</script>

<style>
    .switcher__btn {
        width: 50px;
        height: 50px;
        background: orange;
        border-radius: 0px ;
        font-size: 15px;


    }

</style>