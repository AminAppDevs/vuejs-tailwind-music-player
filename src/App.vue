<template>
  <div class="flex h-screen">
    <div
      class="app-container p-3 m-auto rounded-3xl pt-5 pb-5 bg-opacity-30 bg-white bg-clip-padding shadow-2xl"
      style="backdrop-filter: blur(20px)"
    >
      <img src="./assets/logo.webp" alt="" class="h-24 m-auto mb-3 p-0" />
      <SongList />
    </div>
  </div>
</template>

<script>
import SongList from "./components/SongList.vue";
export default {
  name: "App",
  components: { SongList },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-image: url("./assets/bg.jpg");
  background-position: center center;
  background-size: cover;
  height: 100vh;
}
.app-container {
  width: 400px;
}
</style>
