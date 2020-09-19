<template>
    <div v-swiper:customSlider="swiperOption">
        <div class="swiper-wrapper">
            <div class="swiper-slide" :key="item.id" v-for="item in nowPlaying">
                    <img :src="getImage(item.poster_path)" width="300" height="300" :alt="item.title" />
            </div>
        </div>
        <div class="swiper-button-prev"></div>
        <div class="swiper-button-next"></div>
    </div>

</template>

<script>
    import { movieAPI, apiImage } from "../api";
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
        name: "Movie",
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
              loop: true
            },
            nowPlaying : [],
            popular : [],
            upcoming : []
          }
        },
        directives : {
          swiper : directive
        },
        mounted() {
          movieAPI.nowPlaying()
            .then(([result, error]) => {
              if (error) throw error
              this.nowPlaying = result
            }).catch((error) => console.log(error))
          movieAPI.popular()
            .then(([result, error]) => {
              if (error) throw error
              this.popular = result
            }).catch((error) => console.log(error))
          movieAPI.upcoming()
            .then(([result, error]) => {
              if (error) throw error
              this.upcoming = result
            })
            .catch((error) => console.log(error))
        },
        methods: {
          getImage (path) {
            return apiImage(path)
          }
        }
    }
</script>

<style scoped>

</style>