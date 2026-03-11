<script setup>
const {data: article, pending, error} = await useFetch('http://localhost:3001/articles');
</script>

<template>
  <h1 v-if="pending" class="text-xl font-semibold">Loading...</h1>
  <h1 v-else-if="error" class="text-red-500">Error: {{error}}</h1>

  <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8 p-8">
    <div class="bg-white rounded-xl shadow-md overflow-hidden hover:shadow-xl transition duration-300" v-for="item in article" >
      <img alt="" src="https://picsum.photos/628/250\" class="w-full h-48 object-cover">

      <div class="p-6">
        <h2 class="text-xl font-bold mb-4">{{ item.title }}</h2>

        <NuxtLink :to="`/news/${item.id}`">
          <button class="bg-blue-500 text-white px-4 py-2 rounded-lg hover:bg-blue-600 transition cursor-pointer">Read More</button>
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>