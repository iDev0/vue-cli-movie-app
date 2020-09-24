<template>
  <div id="main-banner">
    <transition name="fade">
      <h1 v-if="show">Amazing Spider!</h1>
    </transition>
    <transition name="fade">
      <div id="button-wrapper" v-if="show">
        <button v-if="show"> ▶️ 재생하기</button>
        <button v-if="show"> ℹ️ 상세정보</button>
      </div>
    </transition>
    <transition name="fade">
      <object
          type="text/html"
          height="500"
          data="//www.youtube.com/embed/2SvwX3ux_-8"
      />
    </transition>
  </div>
</template>

<script>
export default {
  name: "Banner",
  props : {
    show : {
      type : Boolean,
      required : true,
    }
  }
}
</script>

<style scoped>

#main-banner {
  width: 100%;
  height: auto;
}

#main-banner > object {
  width: 100%;
  opacity: 0.3;
}

#main-banner > h1 {
  position: absolute;
  margin-top: 250px;
  font-weight: 900;
  margin-left: 50px;
  z-index: 1;
}

#button-wrapper {
  width: 330px;
  height: 100px;
  border-radius: 10px;
  font-weight: 800;
  font-size: 18px;
  position: absolute;
  z-index: 1;
  margin-top: 320px;
  margin-left: 20px;
}

#button-wrapper > button {
  width: 110px;
  height: 50px;
  margin-right: 10px;
  border-radius: 10px;
  font-weight: 800;
  font-size: 18px;
}

h1 {
  text-align: left;
  color: white;
  padding: 20px;
  font-weight: 800;
}

.fade-enter-active, .fade-leave-active {
  transition: all 1s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(50px);
}
</style>