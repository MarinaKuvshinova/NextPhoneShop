<template>
  <div class="flex flex-col gap-6 text-center max-w-lg mx-auto p-10">
    <Head>
      <Title>Nuxt3 - Iphone{{ name }}</Title>
    </Head>
    <p class="text-2xl">{{ name }}</p>

    <img class="mx-auto" :src="`/images/${name}.jpg`" width="200" alt="" />
    <button
      @click="addToCart"
      class="mx-auto p-3 bg-indigo-900 text-white rounded-md w-40 text-center"
    >
      <span v-if="!inCart()">Buy</span>
      <span v-else>Remove</span>
    </button>

    <!--$route.params.name  -->
  </div>
</template>

<script setup>
const route = useRoute();
const name = computed(() => route.params.name.replaceAll("-", " "));
const fullName = computed(() => `iphone-${route.params.name}`);

// useHead({
//   title: `Nuxt3 - iPhone ${route.params.name}`,
// });

const cart = useCart();
const inCart = () => !!cart.value.find((ct) => ct.name === fullName.value);
function addToCart() {
  if (!inCart()) {
    cart.value.push({
      name: fullName,
    });
  } else {
    cart.value = cart.value.filter((ct) => ct.name !== fullName.value);
  }
}
</script>
