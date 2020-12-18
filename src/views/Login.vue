<template>
  <div class="login">
    <!-- <h3>Please Sign in</h3> -->
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