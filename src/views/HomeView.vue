<script setup>
import { ref, reactive, computed } from "vue";
import axios from "axios";
import VacancyList from "@/components/VacancyList.vue";


const vacancies = reactive([]);

const vacancyTitle = ref("");

const title = computed(() => {
    return vacancyTitle.value.toLowerCase();
});

const showRes = computed(() => {
    return vacancies.length > 0;
});

const getVacancies = async () => {
    await axios
        .get(`https://api.hh.ru/vacancies/?text=${title.value}`, {
            headers: {
                "Content-Type": "application/json",
            },
        })
        .then((res) => {
            console.log(res.data.items);
            vacancies.push(...res.data.items);
        })
        .catch((err) => {
            console.log(err);
        });
};
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

        <form @submit.prevent="getVacancies" class="bg-gray-900 opacity-75 w-full shadow-lg rounded-lg px-8 pt-6 pb-8 mb-4">
            <div class="mb-4">
                <label class="block text-blue-300 py-2 font-bold mb-2" for="emailaddress">
                    Введите название должности, профессии или компании
                </label>
                <input
                    class="shadow appearance-none border rounded w-full p-3 text-gray-700 leading-tight focus:ring transform transition hover:scale-105 duration-300 ease-in-out"
                    v-model="vacancyTitle" id="emailaddress" type="text" placeholder="Example python" />
            </div>

            <div class="flex items-center justify-between pt-4">
                <button
                    class="bg-gradient-to-r from-purple-800 to-green-500 hover:from-pink-500 hover:to-green-500 text-white font-bold py-2 px-4 rounded focus:ring transform transition hover:scale-105 duration-300 ease-in-out">
                    Найти работу
                </button>
            </div>
        </form>
    </div>
    <!--Right Col-->
    <div v-if="showRes" class="w-full xl:w-2/5 overflow-hidden mx-auto">
        <VacancyList :count="vacancies.length" :title="title" :vacancies="vacancies" />
    </div>


    <div v-else class="w-full xl:w-3/5 p-12 overflow-hidden">
        <img class="mx-auto w-full md:w-4/5 transform -rotate-6 transition hover:scale-105 duration-700 ease-in-out hover:rotate-6"
            src="@/assets/resume.png" />
    </div>

</template>
