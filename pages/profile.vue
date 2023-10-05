<template>
  <div>Hello profile</div>
</template>

<script>
definePageMeta({
  layout: "sidebar",
  //inline
  //   middleware: () => {
  //     const auth = useAuth();
  //     return auth.value.isAuthenticated;
  //   },

  middleware: ["auth"],
});
</script>
