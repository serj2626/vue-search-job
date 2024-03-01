<script setup>
import { RouterLink } from "vue-router";
import { reactive, ref } from "vue";
import axios from "axios";
import { useToast } from "vue-toastification";

const toast = useToast();

const url = "https://612d0c196fbb8c08.mokky.dev/register";

const user = reactive({
    name: "",
    email: "",
    password: "",
    password_confirmation: "",
});

const errors = ref([]);

const submitData = async () => {
    if (
        user.username === "" ||
        user.email === "" ||
        user.password === "" ||
        user.password_confirmation === ""
    ) {
        errors.value.push("Все поля обязательны к заполнению");
        toast.error("Все поля обязательны к заполнению");
        return;
    }
    if (user.password !== user.password_confirmation) {
        errors.value.push("Пароли не совпадают");
        return;
    }
    if (user.password.length < 6) {
        errors.value.push("Пароль должен быть больше 6 символов");
        toast.error("Пароль должен быть больше 6 символов");
        return;
    }

    await axios.post(url, {
        username: user.username,
        email: user.email,
        password: user.password,
    })
        .then((res) => {
            localStorage.setItem("token", res.data.token);
            toast.success("Вы успешно зарегистрировались");
            user.username = "";
            user.email = "";
            user.password = "";
            user.password_confirmation = "";
            errors.value = [];
        })
        .catch((err) => {
            console.log(err);
            errors.value.push("Пользователь с таким email уже существует");
            toast.error("Пользователь с таким email уже существует");
        })
};
</script>

<template>
    <div class="w-10/12 mx-auto h-full flex flex-1 justify-center items-center">
        <div class="w-full max-w-lg">
            <div class="leading-loose">
                <form @submit.prevent="submitData" class="max-w-sm m-4 p-10 bg-white bg-opacity-25 rounded-md shadow-xl">
                    <p class="text-center text-3xl font-bold mb-5">
                        <span
                            class="bg-clip-text text-transparent bg-gradient-to-t from-green-300 via-pink-500 to-purple-500">
                            Регистрация
                        </span>
                    </p>
                    <div class="my-2">
                        <label class="block text-sm text-white" for="email">Имя</label>
                        <input class="w-full px-5 py-1 text-gray-700 bg-gray-300 rounded focus:outline-none focus:bg-white"
                            v-model="user.username" type="text" placeholder="Введите почту" aria-label="email" required />
                    </div>
                    <div class="">
                        <label class="block text-sm text-white" for="email">Почта</label>
                        <input class="w-full px-5 py-1 text-gray-700 bg-gray-300 rounded focus:outline-none focus:bg-white"
                            v-model="user.email" type="email" placeholder="Введите почту" aria-label="email" required />
                    </div>

                    <div class="mt-2">
                        <label class="block text-sm text-white">Пароль</label>
                        <input class="w-full px-5 py-1 text-gray-700 bg-gray-300 rounded focus:outline-none focus:bg-white"
                            v-model="user.password" type="password" placeholder="Введите пароль" arial-label="password"
                            required />
                    </div>

                    <div class="mt-2">
                        <label class="block text-sm text-white">Повторите пароль</label>
                        <input class="w-full px-5 py-1 text-gray-700 bg-gray-300 rounded focus:outline-none focus:bg-white"
                            v-model="user.password_confirmation" type="password" placeholder="Введите пароль"
                            arial-label="password" required />
                    </div>

                    <div class="mt-4 items-center flex justify-between">
                        <button
                            class="w-full py-1 text-white font-light tracking-wider bg-rose-500 hover:bg-rose-600 rounded"
                            type="submit">
                            Зарегистрироваться
                        </button>
                    </div>
                    <div class="text-center mt-3 text-lime-400">
                        <RouterLink :to="{ name: 'login' }">Войти в учетную запись</RouterLink>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>
