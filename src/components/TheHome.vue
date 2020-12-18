<template>
  <div id="fondoHome">

    <nav class="navbar navbar-expand-lg navbar-dark bg-dark justify-content-end sticky-top">
      
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">

          <li class="nav-item dropdown ">
            <a class="nav-link dropdown-toggle m-3" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
              Usuario
            </a>
            <div class="dropdown-menu p-3" aria-labelledby="navbarDropdown">
              
              <label class="">Name: {{ user.name }}</label>
                
              <div class="dropdown-divider"></div>

              <label class="">Email: {{ user.email }}</label>
              
              <div class="dropdown-divider"></div>
              
              <button
                class="btn btn-outline-secondary"
                type="button"
                @click="logOut"
                >
                Logout
              </button>

            </div>
          </li>

        </ul>

      </div>
    </nav>

    <h3 class="d-flex justify-content-center mt-5">DATOS DE USUARIO</h3>
    <P class="mt-5">
      Los datos del usuario pueden revisarse en la etiqueta desplegable ubicada en la esquina superior izquierda del menú
    </P>

    <!-- <div>
      <div class="container">
        <nav class="navbar navbar-light bg-light d-flex justify-content-end">
          <button
            class="btn btn-outline-secondary my-2 my-sm-0"
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
              {{ user.name }}
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
    </div> -->

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
#fondoHome{
  background-color:rgb(233, 233, 233);
  /* background-image: url("../../assets/logo.png"); */
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  background-attachment:fixed;
  height: 1000px;
  /* overflow-y: hidden; */
}
</style>