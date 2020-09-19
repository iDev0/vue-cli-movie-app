<template>
    <ul>
        <li :key="item.key" v-for="item in nowPlaying">
            {{ item.title }}
        </li>
    </ul>
</template>

<script>
    import { movieAPI } from "../api";

    export default {
        name: "Movie",
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
        }
    }
</script>

<style scoped>

</style>