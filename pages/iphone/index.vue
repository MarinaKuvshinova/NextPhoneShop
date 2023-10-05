<template>
  <div class="p-10">
    <h1 class="text-6xl text-center mb-7">All iPhones</h1>
    <div class="grid grid-cols-4 gap-4">
      <nuxt-link
        v-for="iphone in iphones"
        :key="`${iphone}`"
        :to="`/iphone/${iphone}`"
        class="shadow-lg text-center p-5 border-2 border-gray-100"
      >
        <h2 class="text-xl mb-4">{{ iphone }}</h2>
        <div class="flex justify-center">
          <img :src="`/images/${iphone}.jpg`" width="200" alt="" />
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<script setup>
useHead({
  title: "Nuxt-3 Iphone",
});
// const { data } = await useFetch("/api/iphone");
// const iphones = data;
const iphones = ["iphone13", "iphone15"];
</script>
