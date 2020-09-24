<template>
    <div id="wrapper">

        <Banner :show="show" />
        <Section title="NowPlaying" :items="nowPlaying"/>
        <Section title="Popular" :items="popular"/>
        <Section title="Upcoming" :items="upcoming"/>
        <Section title="Discover" :items="discover"/>
    </div>
</template>

<script>
    import { movieAPI } from "../api";
    import Section from "@/components/Section";
    import Banner from "@/components/Banner";

    export default {
        name: "Movie",
        components : { Section, Banner },
        data () {
          return {
            nowPlaying : [],
            popular : [],
            upcoming : [],
            discover : [],
            show : false
          }
        },
        mounted() {
          movieAPI.nowPlaying()
            .then(([result, error]) => {
              if (error) throw error
              console.log(result)
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
          movieAPI.discover()
              .then(([result, error]) => {
                if (error) throw error
                this.discover = result
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