<script setup>
import Navbar from "./components/Nabbar.vue";
import Footer from "./components/Footer.vue";
import { RouterView, RouterLink } from "vue-router";
</script>

<template>
  <div class="app leading-normal tracking-normal text-indigo-400 bg-cover bg-fixed"
    style="background-image: url('src/assets/header.png')">
    <div class="h-full app">
      <!--Nav-->
      <Navbar />

      <!--Main-->
      <div class="container pt-24 md:pt-36 mx-auto flex flex-wrap flex-col md:flex-row items-center">
        <!--Left Col-->
        <RouterView />

        <!--Footer-->
        <Footer />
      </div>
    </div>
  </div>
</template>

<style scoped>
.app {
  box-sizing: border-box;
  width: 100%;
  min-height: 100vh;
}
</style>
