<template>
    <div v-swiper:customSlider="swiperOption">
        <div class="swiper-wrapper">
            <div class="swiper-slide" :key="item.id" v-for="item in items">
                <Poster
                    :src="item.poster_path || item.backdrop_path"
                    width="100%"
                    height="auto"
                    :alt="item.title || 'untitle'"
                />
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
      spaceBetween: 5,
      slidesPerGroup: 4
    },
    768: {
      slidesPerView: 3,
      spaceBetween: 5,
      slidesPerGroup: 3
    },
    640: {
      slidesPerView: 2,
      spaceBetween: 5,
      slidesPerGroup: 2
    },
    320: {
      slidesPerView: 1,
      spaceBetween: 5,
      slidesPerGroup: 1
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
          breakpoints: breakPoints,
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
    }
  }
</script>

<style scoped>
</style>