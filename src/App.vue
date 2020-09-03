<template>
  <div id="app">
    <MainLayout></MainLayout>
  </div>
</template>

<script>
import MainLayout from "./components/MainLayout.vue";

export default {
  name: "App",
  components: {
    MainLayout,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,400i,700");
@import url("https://fonts.googleapis.com/css?family=Open+Sans:400,400i,700");

:root {
  height: 100%;
  width: 100%;
  margin: 0;
  padding: 0;
}
html {
  height: 100%;
  width: 100%;
}
body {
  font-family: "Open Sans", sans-serif;
  font-size: 14px;
  height: 100%;
  width: 100%;
  background: #cfd8dc;
  cursor: default !important;
  user-select: none;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
  width: 100%;
}

</style>
