<script setup>
defineProps({
  vacancies: {
    type: Array,
    required: false,
  },
  title: {
    type: String,
    required: false,
  },
  count: {
    type: Number,
    required: false,
  },
});
</script>

<template>
  <div class="text-center mb-12">
    <span
      class="text-3xl bg-clip-text text-transparent bg-gradient-to-r from-green-400 via-pink-500 to-purple-500"
      >{{ count }} вакансий «{{ title }}»
    </span>
  </div>

  <div
    class="card border-r-8 bg-red-100 border-indigo-200 border-r-pink-700"
    v-for="vacancy in vacancies"
    :key="vacancy.id"
  >
    <card class="flex flex-col">
      <div class="card-title text-2xl text-pink-500 mb-3">
        {{ vacancy.name }}
      </div>
      <div class="flex">
        <div class="card-employer text-purple-800 mb-3">
          {{ vacancy.employer.name }}
        </div>
        <div class="card-area text-purple-800 mb-3 ms-10">
          {{ vacancy.area.name }}
        </div>
      </div>
      <div class="flex justify-items-center my-3">
        
        <img src="@/assets/icons/work_history.ico" />
        <div class="card-experience text-purple-800 mx-3">
          {{ vacancy.experience.name }}
        </div>
      </div>

      <a
        :href="vacancy.alternate_url"
        target="_blank"
        class="bg-purple-600 hover:bg-purple-700 hover:cursor-pointer"
      >
        Подробнее
      </a>
    </card>
  </div>
</template>

<style scoped>
.card {
  padding: 15px 15px;
  border-radius: 5px;
  margin-bottom: 15px;
}

a {
  padding: 5px 10px;
  border-radius: 5px;
  color: white;
  text-align: center;
}
</style>
