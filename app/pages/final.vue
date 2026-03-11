<script setup>
const formData = useState('contactFormData')
</script>

<template>
  <div class="min-h-screen bg-gray-100">

    <div class="flex justify-center items-center px-6 py-16">
      <div class="bg-white rounded-xl shadow-md p-10 max-w-2xl w-full text-center">

        <h1 class="text-3xl font-bold mb-6">
          Thank you {{ formData.firstName }}!
        </h1>

        <p class="text-gray-700 text-lg mb-8">
          Thank you for your question or feedback.
          We will contact you as soon as possible at
          <span class="font-semibold">{{ formData.mail }}</span>.
        </p>

        <NuxtLink
            to="/"
            class="inline-block bg-blue-500 text-white px-6 py-2 rounded-lg hover:bg-blue-600 transition cursor-pointer"
        >
          Back to Home
        </NuxtLink>

      </div>
    </div>
  </div>
</template>

<style scoped>
</style>