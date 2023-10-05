<template>
  <nav class="bg-purple-700 text-white shadow-lg p-3 text-lg flex gap-3">
    <NuxtLink to="/">Home</NuxtLink>
    <NuxtLink to="/about">About</NuxtLink>
    <NuxtLink to="/iphone">iPhones</NuxtLink>
    <div v-if="auth.isAuthenticated" class="flex gap-3">
      <NuxtLink to="/profile">Profile</NuxtLink>
      <button @click="logOut">Login Out</button>
    </div>
    <NuxtLink v-else to="/login">Login</NuxtLink>
    <div class="ml-auto flex gap-3">
      <p>Cart ({{ cart.length }})</p>
      <p>Visited ({{ pageVisitCount }})</p>
    </div>
  </nav>
</template>

<script setup>
const cart = useCart();
const auth = useAuth();
const pageVisitCount = usePageVisitCount();
function logOut() {
  auth.value.isAuthenticated = false;
}
</script>
