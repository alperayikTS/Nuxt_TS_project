<script setup>
const {data: article, pending, error} = await useFetch('http://localhost:3001/articles');

const newsInput = ref('')
const tempArr = ref([])

function handleSearch() {
  if (newsInput.value === '') {
    alert('zoekbalk is leeg vul aub iets in')
  } else {
    const filteredTitle = article.value.filter(item => item.title.toLowerCase().includes(newsInput.value.toLowerCase()))
    tempArr.value = filteredTitle
  }
}

const currentData = computed(() => {
  if (tempArr.value.length >= 1) {
    return tempArr.value
  } else {
    return article.value
  }
})

watch(newsInput, () => {
  if(newsInput.value.length <= 1) {
    tempArr.value = article.value
  }
})
</script>

<template>
  <h1 v-if="pending" class="text-xl font-semibold">Loading...</h1>
  <div v-else-if="error">
    <h1 class="flex justify-center text-xl font-semibold mt-20">Er is wat fout gegaan bij het ophalen van de Data</h1>
  </div>


  <div class="mt-10" v-else-if="article">
    <div class="flex justify-center text-xl font-semibold">
      <input class="border-2 rounded-2xl p-3" type="text" v-model="newsInput">
      <button class="bg-blue-500 text-white px-4 py-2 rounded-lg hover:bg-blue-600 transition cursor-pointer ml-2" @click="handleSearch">Zoeken</button>
    </div>
    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8 p-8">
      <div class="bg-white rounded-xl shadow-md overflow-hidden hover:shadow-xl transition duration-300"
           v-for="item in currentData">
        <img alt="" src="https://picsum.photos/628/250\" class="w-full h-48 object-cover">

        <div class="p-6">
          <h2 class="text-xl font-bold mb-4">{{ item.title }}</h2>

          <NuxtLink :to="`/news/${item.id}`">
            <button class="bg-blue-500 text-white px-4 py-2 rounded-lg hover:bg-blue-600 transition cursor-pointer">Read
              More
            </button>
          </NuxtLink>
        </div>
      </div>
    </div>
  </div>
  <div v-else>
    <div class="flex justify-center text-xl font-semibold mt-20">
      <h1>Op dit moment kunnen er geen nieuws artikelen worden getoond probeer het later opnieuw</h1>
    </div>
  </div>
</template>

<style scoped>
</style>