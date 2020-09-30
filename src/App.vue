<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">홈</router-link>
      <router-link to="/movie">영화</router-link>
      <router-link to="/tv">TV프로그램</router-link>
      <font-awesome-layers :style="{float : 'right'}">
        <font-awesome-icon icon="search" :style="{ color: 'white' }" size="lg" />
      </font-awesome-layers>

    </div>
    <router-view/>
  </div>
</template>

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
