<template>
  <div id="wrapper">
      <Banner title="LUCIFER" :show="show" youtube-key="X4bF_quwNtw" />
      <Section title="Today" :items="today"/>
      <Section title="ThisWeek" :items="thisWeek"/>
      <Section title="TopRated" :items="topRated"/>
      <Section title="Popular" :items="popular"/>/>
  </div>
</template>

<script>
import Section from "@/components/Section";
import Banner from "@/components/Banner";
import { tvAPI } from "@/api";
export default {
  name: "TV.vue",
  components : { Section, Banner },
  data() {
    return {
      show : false,
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
        console.log(results)
        this.popular = results
      }).catch(error => {
        console.log(error)
      })
    this.show = true
  }

}
</script>

<style scoped>

</style>