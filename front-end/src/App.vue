<template>
  <div id="app">
    <Header/>
    <Menu/>
  </div>
</template>

<script>
//import HelloWorld from "./components/HelloWorld.vue";
import Header from "./components/Header.vue";
import Menu from "./components/Menu.vue";

export default {
  name: "App",
  components: {
    Header, Menu
  },
};
</script>

<style lang="scss">
*{
  margin:0;
  padding:0;
  box-sizing: border-box;
}
body{
  background-color: #FBFBFB;
  font-family: sans-serif;
}
// #app {
//   font-family: Avenir, Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
//   margin-top: 60px;
// }
</style>
