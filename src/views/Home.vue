<template>
  <div id="wrapper">
    <Banner title="After We Collided" :show="show" youtube-key="BJBxXDhpZq0" />
    <Section title="현재 상영중인 영화" :items="nowPlaying"/>
    <Section title="인기있는 영화" :items="popular"/>
    <Section title="가장 인기있는 TV 프로그램" :items="topRated"/>
    <Section title="새롭게 추가된 TV 프로그램" :items="today"/>
  </div>
</template>

<script>
import { movieAPI, tvAPI } from "../api";
import Section from "@/components/Section";
import Banner from "@/components/Banner";

export default {
  name: "Home",
  components : { Section, Banner },
  data () {
    return {
      nowPlaying : [],
      popular : [],
      today : [],
      topRated : [],
      show : false
    }
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
    tvAPI.today()
        .then(([result, error]) => {
          if (error) throw error
          this.today = result
        })
        .catch((error) => console.log(error))
    tvAPI.topRated()
        .then(([result, error]) => {
          if (error) throw error
          this.topRated = result
        })
        .catch((error) => console.log(error))
    this.show = !this.show
  },
}
</script>

<style scoped>
#wrapper {
  width: 100%;
  height: auto;
}
</style>