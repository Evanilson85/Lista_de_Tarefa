<template>
  <div id="app">
    <Header />
    <Main />

    <footer></footer>
  </div>
</template>

<script>
//import HelloWorld from "./components/HelloWorld.vue";
import Header from "./components/header/Header";
import Main from "./components/main/mainInput";

export default {
  name: "App",
  components: {
    //  HelloWorld,
    Main,
    Header,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0%;
  box-sizing: border-box;
  outline: none;
  list-style: none;
  text-decoration: none;
}
#app {
  height: auto;
}
body {
  background-color: #1e1e1e;
}
.teste {
  color: #666565;
  background-color: #ff760c;
}
footer {
  margin: 30px 0;
  height: 200px;
}
</style>
