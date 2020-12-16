<template>
  <div>
    <div class="container">
      <nav class="navbar navbar-light bg-light d-flex justify-content-end">
        <button
          class="btn btn-outline-success my-2 my-sm-0"
          type="button"
          @click="logOut"
        >
          logOut
        </button>
      </nav>
    </div>
    <div class="container">
      <div class="row mb-3">
        <label class="col-sm-2">Name</label>
        <div class="col-sm-10 border border-primary rounded-pill">
          <p class="m-0">
            {{ user.nombre }}
          </p>
        </div>
      </div>
      <div class="row mb-3">
        <label class="col-sm-2">Email</label>
        <div class="col-sm-10 border border-primary rounded-pill">
          <p class="m-0">
            {{ user.email }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {},
    };
  },
  methods: {
    getUserDetails() {
      let user = localStorage.getItem("user");
      let token = localStorage.getItem("jwt");
      if (token) {
        this.user = JSON.parse(user);
      }
    },
    logOut() {
      localStorage.removeItem("jwt");
      localStorage.removeItem("user");
      this.$router.push("/");
    },
  },
  created() {
    this.getUserDetails();
  },
};
</script>

<style>
</style>