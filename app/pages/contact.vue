<script setup>
let firstName = ref('')
let lastName = ref('')
let mail = ref('')
let text = ref('')

const formData = useState('contactFormData', () => ({
  firstName: '',
  lastName: '',
  mail: '',
  text: ''
}))

function userSend() {
  if (!firstName.value || !lastName.value || !mail.value || !text.value) {
    alert('input is empty')
    return
  }

  formData.value = {
    firstName: firstName.value,
    lastName: lastName.value,
    mail: mail.value,
    text: text.value,
  }

  clearInputs()
  navigateTo('/final')
}

function clearInputs() {
  firstName.value = ''
  lastName.value = ''
  mail.value = ''
  text.value = ''
}
</script>

<template>
  <div class="min-h-screen bg-gray-100">
    <navbar />

    <div class="max-w-3xl mx-auto px-6 py-10">
      <h1 class="text-3xl font-bold text-center mb-8">Contact page</h1>

      <div class="bg-white rounded-xl shadow-md p-8">
        <form @submit.prevent="userSend" class="flex flex-col gap-5">
          <div>
            <label class="block mb-2 font-semibold text-gray-700">Firstname:</label>
            <input
                type="text"
                placeholder="firstname"
                v-model="firstName"
                class="w-full border border-gray-300 rounded-lg px-4 py-3 focus:outline-none focus:ring-2 focus:ring-blue-500"
            />
          </div>

          <div>
            <label class="block mb-2 font-semibold text-gray-700">Lastname:</label>
            <input
                type="text"
                placeholder="lastname"
                v-model="lastName"
                class="w-full border border-gray-300 rounded-lg px-4 py-3 focus:outline-none focus:ring-2 focus:ring-blue-500"
            />
          </div>

          <div>
            <label class="block mb-2 font-semibold text-gray-700">Email:</label>
            <input
                type="text"
                placeholder="example@mail.com"
                v-model="mail"
                class="w-full border border-gray-300 rounded-lg px-4 py-3 focus:outline-none focus:ring-2 focus:ring-blue-500"
            />
          </div>

          <div>
            <label class="block mb-2 font-semibold text-gray-700">Text:</label>
            <textarea
                placeholder="Put your message here..."
                v-model="text"
                rows="5"
                class="w-full border border-gray-300 rounded-lg px-4 py-3 focus:outline-none focus:ring-2 focus:ring-blue-500 resize-none"
            ></textarea>
          </div>

          <div class="flex gap-4 pt-2">
            <button
                type="submit"
                class="bg-blue-500 text-white px-5 py-2 rounded-lg hover:bg-blue-600 transition cursor-pointer"
            >
              Submit
            </button>

            <NuxtLink to="/">
              <button
                  type="button"
                  class="bg-blue-500 text-white px-5 py-2 rounded-lg hover:bg-blue-600 transition cursor-pointer"
              >
                Back
              </button>
            </NuxtLink>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>