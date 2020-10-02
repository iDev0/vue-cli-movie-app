<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">홈</router-link>
      <router-link to="/movie">영화</router-link>
      <router-link to="/tv">TV프로그램</router-link>
      <SearchBar :keyword="keyword" @search="value => search(value)" />
    <router-view/>
    </div>
  </div>
</template>

<script>
// import { movieAPI, tvAPI } from "@/api";
import SearchBar from "@/components/SearchBar";

export default {
  components: {SearchBar},
  data () {
    return {
      keyword: ''
    }
  },
  methods : {
    search(keyword) {
      if (keyword !== this.$router.currentRoute.query.keyword) {
        this.$router.replace({path : 'search', query : { keyword : keyword }});
      }

      // movieAPI.search(this.keyword)
      //   .then(([results, err]) => {
      //     if (err) throw err
      //     console.log(results)
      //     // this.$router.push({path : 'search', params : results })
      //   })
      //   .catch(err => console.log(err))
      //
      // tvAPI.search(this.keyword)
      //   .then(([results, err]) => {
      //     if (err) throw err
      //     console.log(results)
      //   })
      //   .catch(err => console.log(err))
    }
  }
}
</script>

<style>
body {
  background: black;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
  text-align: left;
}

#nav a {
  font-weight: bold;
  color: white;
  margin-right: 20px;
  font-size: 18px;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
