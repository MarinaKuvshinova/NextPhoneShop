<template>
  <form
    @submit.prevent="onSubmit"
    class="flex flex-col gap-7 pt-10 mx-auto max-w-xl"
  >
    <div v-if="_error">
      <p class="bg-red-600 text-white rounded-md p-2 text-sm">{{ _error }}</p>
    </div>
    <div>
      <input
        type="email"
        class="block w-full px-4 py-2 text-xl font-normal text-gray-700 bg-white bg-clip-padding border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none"
        placeholder="Email"
        v-model="form.email"
      />
    </div>
    <div>
      <input
        type="password"
        class="block w-full px-4 py-2 text-xl font-normal text-gray-700 bg-white bg-clip-padding border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none"
        placeholder="Password"
        v-model="form.password"
      />
    </div>
    <button
      type="submit"
      class="inline-block px-7 py-3 bg-blue-600 text-white font-medium text-sm leading-snug uppercase shadow-md hover:bg-blue-700 hover:shadow-lg focus:bg-blue-700 focus:shadow-lg focus:outline-none focus:right-0 active:bg-blue-800 active:shadow-lg transition duration-150 ease-in-out w-44 rounded-lg"
    >
      <span v-if="isLoading">Loading...</span>
      <span v-else>Sign In</span>
    </button>
  </form>
</template>

<script setup>
const url = "https://reqres.in/api/login";
const form = reactive({
  email: "eve.holt@reqres.in",
  password: "cityslicka ",
});
const isLoading = ref(false);
const _error = ref(null);

async function onSubmit() {
  if (isLoading.value) return;
  isLoading.value = true;
  const { data, error } = await useFetch(url, {
    method: "post",
    body: form,
  });

  isLoading.value = false;
  if (error.value) {
    _error.value = error.value.data.error;
    return;
  }

  const auth = useAuth();
  auth.value.isAuthenticated = true;

  navigateTo("/");
}
</script>
