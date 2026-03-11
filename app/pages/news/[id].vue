<script setup>
import navbar from "~/components/navbar.vue";

const route = useRoute()
const id = route.params.id

const {data: article, pending, error} = await useFetch(
    `http://localhost:3001/articles/${id}`
)
</script>

<template>
  <navbar/>

  <div class="min-h-screen bg-gray-100 py-10">
    <div class="max-w-3xl mx-auto px-6">

      <p v-if="pending" class="text-lg font-semibold">Loading...</p>

      <p v-else-if="error" class="text-red-500">
        Could not load article
      </p>

      <div
          v-else-if="article"
          class="bg-white rounded-xl shadow-md p-8"
      >
        <h1 class="text-3xl font-bold mb-4">
          {{ article.title }}
        </h1>

        <p class="text-gray-700 leading-relaxed mb-6">
          {{ article.description }}
        </p>

        <small class="text-gray-400 block mb-6">
          {{ article.date }}
        </small>

        <NuxtLink
            to="/"
            class="inline-block bg-blue-500 text-white px-4 py-2 rounded-lg hover:bg-blue-600 transition"
        >
          ← Back
        </NuxtLink>
      </div>

    </div>
  </div>
</template>