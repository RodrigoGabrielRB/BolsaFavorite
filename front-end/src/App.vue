<template>
  <div id="app">
    <Header/>
    <Menu/>
    <Navigator/>
    <Content/>
    <Footer/>
  </div>
</template>

<script>
//import HelloWorld from "./components/HelloWorld.vue";
import Header from "./components/Header.vue";
import Menu from "./components/Menu.vue";
import Navigator from "./components/Navigator.vue";
import Content from "./components/Content.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Header, Menu, Footer, Navigator, Content,
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
