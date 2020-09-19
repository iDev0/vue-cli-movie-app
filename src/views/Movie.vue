<template>
    <div>
        <h1>하하하</h1>
        <Slider :items="nowPlaying" />
        <h1>하하하1</h1>
        <Slider :items="popular" />
        <h1>하하하2</h1>
        <Slider :items="upcoming" />
    </div>
</template>

<script>
    import { movieAPI } from "../api";
    import Slider from "../components/Slider";
    export default {
        name: "Movie",
        components : { Slider },
        data () {
          return {
            nowPlaying : [],
            popular : [],
            upcoming : []
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
          movieAPI.upcoming()
            .then(([result, error]) => {
              if (error) throw error
              this.upcoming = result
            })
            .catch((error) => console.log(error))
        },
    }
</script>

<style scoped>

</style>