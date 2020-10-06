<template>
    <img
        ref="img"
        :src="path"
        :width="width"
        :height="height"
        :alt="alt"
    />
</template>

<script>
    import { apiImage } from "../api";

    export default {
    name: "Poster",
    props : {
      src : {
        type : String,
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
    },
  }
</script>

<style scoped>
img {


}

img:hover {
  transition-duration: 1s;
  -webkit-transform: scale(1.5);
  -ms-transform: scale(1.5);
  -o-transform: scale(1.5);
  transform: scale(1.5);
  z-index: 9999;
}

</style>