<template>
  <div class="login mt-3">
    <h3>Please Signin</h3>
    <the-login></the-login>
  </div>
</template>

<script>
import TheLogin from "../components/auth/TheLogin.vue";
export default {
  name: "Signin",
  components: {
    TheLogin,
  },
};
</script>

<style>
</style>