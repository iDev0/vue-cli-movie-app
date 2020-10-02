<template>
    <div id="container">
      <font-awesome-layers id="icon-container">
        <font-awesome-icon icon="search" :style="{ color: 'white' }" size="lg" />
      </font-awesome-layers>
      <input
          id="search-bar"
          type="text"
          placeholder="검색어를 입력해 주세요."
          v-model="value"
          v-on:keyup.enter="search()" />
    </div>
</template>

<script>
export default {
  name: "SearchBar",
  props : {
    keyword : {
      type : String,
      required : true
    }
  },
  data () {
    return {
      value : this.keyword
    }
  },
  methods : {
    search() {
      this.$emit('search', this.value);
    }
  }
}
</script>

<style scoped>
#container {
  float: right;
  border: 1px solid white;
  text-align: center;
}

#icon-container {
  text-align: center;
  width: 20px;
  padding-right: 5px
}


#search-bar {
  background: transparent;
  border-radius: 5px;
  height: 25px;
  width: 200px;
  border-right: transparent;
  color: white;
}
</style>