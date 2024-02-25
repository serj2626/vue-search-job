<script setup>
import { RouterLink } from "vue-router";
</script>

<template>
  <div class="w-10/12 mx-auto h-full flex flex-1 justify-center items-center">
    <div class="w-full max-w-lg">
      <div class="leading-loose">
        <form
          class="max-w-sm m-4 p-10 bg-white bg-opacity-25 rounded shadow-xl"
        >
          <p class="text-white text-center text-lg font-bold mb-5">Создать аккаунт</p>
          <div class="">
            <label class="block text-sm text-white" for="email">Почта</label>
            <input
              class="w-full px-5 py-1 text-gray-700 bg-gray-300 rounded focus:outline-none focus:bg-white"
              type="email"
              placeholder="Введите почту"
              aria-label="email"
              required
            />
          </div>

          <div class="mt-2">
            <label class="block text-sm text-white">Пароль</label>
            <input
              class="w-full px-5 py-1 text-gray-700 bg-gray-300 rounded focus:outline-none focus:bg-white"
              type="password"
              placeholder="Введите пароль"
              arial-label="password"
              required
            />
          </div>


          <div class="mt-2">
            <label class="block text-sm text-white">Повторите пароль</label>
            <input
              class="w-full px-5 py-1 text-gray-700 bg-gray-300 rounded focus:outline-none focus:bg-white"
              type="password"
              placeholder="Введите пароль"
              arial-label="password"
              required
            />
          </div>

          <div class="mt-4 items-center flex justify-between">
            <button
              class="w-full py-1 text-white font-light tracking-wider bg-rose-500 hover:bg-rose-600 rounded"
              type="submit"
            >
              Зарегистрироваться
            </button>

          </div>
          <div class="text-center mt-3 text-lime-400">
            <RouterLink :to="{ name: 'login' }" >Войти в учетную запись</RouterLink>
            

          </div>
        </form>
      </div>
    </div>
  </div>
</template>
