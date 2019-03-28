<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">home</router-link> |
      <router-link to="/writeNote">writeNote</router-link>
    </div> -->
    <router-view/>
  </div>
</template>

<style lang="scss">
html,body{
  margin: 0;
  padding: 0;
  width:100%;
  height: 100%;
  overflow-x:hidden;
}
#app {
  height: 100%;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
