<template>
  <div id="wrapper">
      <Section title="Today" :items="today"/>
      <Section title="ThisWeek" :items="thisWeek"/>
      <Section title="TopRated" :items="topRated"/>
      <Section title="Popular" :items="popular"/>/>
  </div>
</template>

<script>
import Section from "@/components/Section";
import { tvAPI } from "@/api";
export default {
  name: "TV.vue",
  components : { Section },
  data() {
    return {
      today : [],
      thisWeek : [],
      topRated : [],
      popular : [],
    }
  },
  mounted() {
    tvAPI.today()
      .then(([results, error]) => {
        if (error) throw error
        this.today = results
      }).catch(error => {
        console.log(error)
      })
    tvAPI.thisWeek()
      .then(([results, error]) => {
        if (error) throw error
        this.thisWeek = results
      }).catch(error => {
        console.log(error)
      })
    tvAPI.topRated()
      .then(([results, error]) => {
        if (error) throw error
        this.topRated = results
      }).catch(error => {
        console.log(error)
      })
    tvAPI.popular()
      .then(([results, error]) => {
        if (error) throw error
        this.popular = results
      }).catch(error => {
        console.log(error)
      })

  }

}
</script>

<style scoped>

</style>