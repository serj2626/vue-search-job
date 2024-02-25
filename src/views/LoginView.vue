<script setup></script>

<template>
  <div class="container mx-auto h-full flex flex-1 justify-center items-center">
    <div class="w-full max-w-lg">
      <div class="leading-loose">
        <form
          class="max-w-sm m-4 p-10 bg-white bg-opacity-25 rounded shadow-xl"
        >
          <p class="text-white text-center text-lg font-bold mb-5">Авторизация</p>
          <div class="">
            <label class="block text-sm text-white" for="email">Почта</label>
            <input
              class="w-full px-5 py-1 text-gray-700 bg-gray-300 rounded focus:outline-none
               focus:bg-white"
              type="email"
 
              placeholder="Введите почту"
              aria-label="email"
              required
            />
          </div>
          <div class="mt-2">
            <label class="block text-sm text-white">Пароль</label>
            <input
              class="w-full px-5 py-1 text-gray-700 bg-gray-300 rounded focus:outline-none
               focus:bg-white"
              type="password"

              placeholder="Введите пароль"
              arial-label="password"
              required
            />
          </div>

          <div class="mt-4 items-center flex justify-between">
            <button
              class="px-4 py-1 text-white font-light tracking-wider bg-rose-500 hover:bg-rose-600 rounded"
              type="submit"
            >
              Войти
            </button>
            <a
              class="inline-block right-0 align-baseline font-bold text-sm text-500 text-white hover:text-red-400"
              href="#"
              >Забыли пароль ?</a
            >
          </div>
          <div class="text-center mt-3 text-lime-400">
            <RouterLink :to="{ name: 'signup' }" >Создать учетную запись</RouterLink>
            

          </div>
        </form>
      </div>
    </div>
  </div>
</template>
