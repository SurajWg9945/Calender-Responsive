<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Calender />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Calender from "./components/calender.vue";

export default {
  name: "App",
  components: {
    Calender,
  },
};
</script>

<style>
body {
  margin: 0px;
}
#app {
  background: #f9e4c5;
  height: 100vh;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
@media (min-width: 320px) and (max-width: 480px) {
  #app {
    align-items: normal;
    padding-top: 6rem;
  }
}
</style>
