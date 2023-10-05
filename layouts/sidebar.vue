<template>
  <div class="main bg-green-100">
    <ul class="sidebar">
      <li>Dashbord</li>
      <li>Settings</li>
    </ul>
    <section>
      <slot></slot>
    </section>
  </div>
</template>

<style>
.main {
  display: flex;
  gap: 20px;
}

.sidebar {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
</style>
