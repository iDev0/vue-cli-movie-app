<template>
    <img :src="path" :width="width" :height="height" :alt="alt" />
</template>

<script>
    import { apiImage } from "../api";

    export default {
    name: "Poster",
    props : {
      src : {
        type : String,
        required : true
      },
      alt : {
        type : String,
        required : true
      },
      width : { type : String },
      height : { type : String }
    },
    computed : {
      path () {
        return apiImage(this.src)
      }
    }
  }
</script>

<style scoped>

</style>