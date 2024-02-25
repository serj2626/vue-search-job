<script setup>
import { RouterLink } from 'vue-router';
</script>


<template>
  <!--Nav-->
  <div class="w-full container mx-auto pt-6">
    <div class="w-full flex items-center justify-between">

      <RouterLink :to="{ name: 'home' }" class="link">
        <p class="flex items-center text-indigo-400 no-underline hover:no-underline
       font-bold text-2xl lg:text-4xl" href="#">
          Job<span
            class="bg-clip-text text-transparent bg-gradient-to-r from-green-400
             via-pink-500 to-purple-500">Search</span>
        </p>
      </RouterLink>




      <div class="flex w-1/2 justify-end content-center">
        <RouterLink :to="{ name: 'about' }" class="link">
          <img src="@/assets/icons/about.ico" alt="" class="h-8">
        </RouterLink>
        <RouterLink to="/" class="link">
          <img src="@/assets/icons/resume.ico" alt="" class="h-8">
        </RouterLink>
        <RouterLink :to="{ name: 'login' }" class="link">
          <img src="@/assets/icons/user.ico" alt="" class="h-8">
        </RouterLink>
      </div>
    </div>
  </div>
</template>

<style scoped>
.link {
  margin: 0 10px;
}
</style>
