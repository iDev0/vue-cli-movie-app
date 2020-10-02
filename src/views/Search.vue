<template>
  <div id="wrapper">
    <Section title="영화" :items="movieSearchResults"/>
    <Section title="TV프로그램" :items="tvSearchResults"/>
  </div>
</template>

<script>
import Section from "@/components/Section";
import { movieAPI, tvAPI } from "@/api";
export default {
  name: "Search",
  components : { Section },
  data() {
    return {
      movieSearchResults: [],
      tvSearchResults: []
    }
  },
  mounted() {
    this.searchData()
  },
  watch : {
    '$route' : function () {
      this.searchData()
    }
  },
  methods : {
    searchData() {

      const keyword = this.$router.currentRoute.query.keyword

      movieAPI.search(keyword)
        .then(([results, err]) => {
          if (err) throw err
          this.movieSearchResults = results
          console.log(results)
        })
        .catch(err => console.log(err))

      tvAPI.search(keyword)
        .then(([results, err]) => {
          if (err) throw err
          this.tvSearchResults = results
          console.log(results)
        })
        .catch(err => console.log(err))
    }
  }

}
</script>

<style scoped>
#wrapper {
  width: 100%;
  height: auto;
}
</style>