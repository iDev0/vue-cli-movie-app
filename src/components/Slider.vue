<template>
    <div v-swiper:customSlider="swiperOption">
        <div class="swiper-wrapper">
            <div class="swiper-slide" :key="item.id" v-for="item in items">
                <Poster :src="item.poster_path" width="300" height="300" :alt="item.title" />
            </div>
        </div>
        <div class="swiper-button-prev"></div>
        <div class="swiper-button-next"></div>
    </div>
</template>

<script>
  import Poster from "../components/Poster";
  import { directive } from 'vue-awesome-swiper'
  import 'swiper/css/swiper.css'

  const breakPoints = {
    1024: {
      slidesPerView: 4,
      spaceBetween: 40
    },
    768: {
      slidesPerView: 3,
      spaceBetween: 30
    },
    640: {
      slidesPerView: 2,
      spaceBetween: 20
    },
    320: {
      slidesPerView: 1,
      spaceBetween: 10
    }
  }

  export default {
    name: "Slider",
    components: { Poster },
    props : {
      items : {
        type : Array,
        required : true,
      }
    },
    data () {
      return {
        swiperOption : {
          slidesPerView: 4,
          spaceBetween: 50,
          slidesPerGroup: 4,
          breakPoints: breakPoints,
          navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev',
          },
          lazy: true,
          loop: true,
        },
      }
    },
    directives : {
      swiper : directive
    },
  }
</script>

<style scoped>

</style>