<template>
  <div class="home mt-3">
    <h3>Datos del usuario</h3>
    <the-home></the-home>
  </div>
</template>

<script>
// @ is an alias to /src
import TheHome from "../components/TheHome.vue";

export default {
  name: "Home",
  components: {
    TheHome,
  },
};
</script>
