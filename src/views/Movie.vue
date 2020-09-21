<template>
    <div id="wrapper">
        <div id="main-banner">
            <transition name="fade">
              <h1 v-if="show">나는야 <br/> 스파이더맨</h1>
            </transition>
            <transition name="fade">
              <div id="button-wrapper" v-if="show">
                <button v-if="show"> ▶️ 재생하기</button>
                <button v-if="show"> ℹ️ 상세정보</button>
              </div>
            </transition>

            <img src="https://images.unsplash.com/photo-1534375971785-5c1826f739d8?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80" />
        </div>

        <h1>NowPlaying</h1>
        <Slider :items="nowPlaying" />
        <h1>Popular</h1>
        <Slider :items="popular" />
        <h1>Upcoming</h1>
        <Slider :items="upcoming" />
        <h1>Discover</h1>
        <Slider :items="discover" />
    </div>
</template>

<script>
    import { movieAPI } from "../api";
    import Slider from "../components/Slider";
    export default {
        name: "Movie",
        components : { Slider },
        data () {
          return {
            nowPlaying : [],
            popular : [],
            upcoming : [],
            discover : [],
            show : false
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
          movieAPI.discover()
              .then(([result, error]) => {
                if (error) throw error
                this.discover = result
              })
              .catch((error) => console.log(error))
          this.show = !this.show
        },
    }
</script>

<style scoped>
#wrapper {
  width: 100%;
  height: auto;
}

#main-banner {
  width: 100%;
  height: auto;
}

#main-banner > img {
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
  margin-top: 370px;
  margin-left: 24px;
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