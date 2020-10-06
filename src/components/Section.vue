<template>
  <div>
    <h1>{{title}}</h1>
    <Slider :items="items" />
  </div>
</template>

<script>
import Slider from "@/components/Slider";
export default {
  name: "Section",
  components : { Slider },
  props : {
    title : {
      type : String,
      required: true,
    },
    items : {
      type : Array,
      required: true
    },
  }
}
</script>

<style scoped>
h1 {
  text-align: left;
  color: white;
  padding: 20px;
  font-weight: 800;
}
</style>