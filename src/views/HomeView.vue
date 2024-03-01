<script setup>
import RightComponent from '@/components/RightComponent.vue';
</script>


<template>
    <div class="flex flex-col w-full xl:w-2/5 justify-center lg:items-start overflow-y-hidden">
        <h1 class="my-4 text-3xl md:text-5xl text-white opacity-75 font-bold leading-tight text-center md:text-left">
            Легкий
            <span class="bg-clip-text text-transparent bg-gradient-to-r from-green-400 via-pink-500 to-purple-500">
                поиск
            </span>
            вакансий и стажировок для IT специалистов
        </h1>
        <p class="leading-normal text-base md:text-2xl mb-8 text-center md:text-left">
            Введите название должности, профессии или компании!
        </p>

        <form class="bg-gray-900 opacity-75 w-full shadow-lg rounded-lg px-8 pt-6 pb-8 mb-4">
            <div class="mb-4">
                <label class="block text-blue-300 py-2 font-bold mb-2" for="emailaddress">
                    Введите название должности, профессии или компании
                </label>
                <input class="shadow appearance-none border rounded w-full p-3 text-gray-700
                     leading-tight focus:ring transform transition hover:scale-105 duration-300
                      ease-in-out" id="emailaddress" type="text" placeholder="python" />
            </div>

            <div class="flex items-center justify-between pt-4">
                <button
                    class="bg-gradient-to-r from-purple-800 to-green-500 hover:from-pink-500 hover:to-green-500 text-white font-bold py-2 px-4 rounded focus:ring transform transition hover:scale-105 duration-300 ease-in-out"
                    type="button">
                    Подписаться
                </button>
            </div>
        </form>
    </div>

    <!--Right Col-->
    <RightComponent />
</template>