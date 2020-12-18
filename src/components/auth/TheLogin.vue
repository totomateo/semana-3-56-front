<template>
  <div id="fondoLogin" class="d-flex align-items-center justify-content-center">

    <div id="fondoFormulario" class="container p-4">
      <h3 class="mb-4 text-muted">
        Sign in
      </h3>
      <form>
        <div class="mb-3">
          <!-- <label for="exampleInputEmail1" class="form-label">Email address</label> -->
          <input
            v-model="signin.email"
            type="email"
            class="form-control"
            id="exampleInputEmail1"
            aria-describedby="emailHelp"
            placeholder="Email address"
          />
          <div id="emailHelp" class="form-text">
            <small>
              We'll never share your email with anyone else.
            </small>
          </div>
        </div>
        <div class="mb-4">
          <!-- <label for="exampleInputPassword1" class="form-label">Password</label> -->
          <input
            v-model="signin.password"
            type="password"
            class="form-control"
            id="exampleInputPassword1"
            placeholder="Password"
          />
          <!-- <pre>
              {{ signin }}
          </pre> -->
        </div>
        <button 
        @click.prevent="signinUser" 
        type="submit" 
        class="btn btn-dark w-100">
          Sign in
        </button>
      </form>
    </div>

  </div>
</template>

<script>
import swal from "sweetalert";
export default {
  name: "TheLogin",
  data() {
    return {
      signin: {
        email: "",
        pasword: "",
      },
    };
  },
  methods: {
    async signinUser() {
      try {
        let response = await this.$http.post("/api/auth/signin", this.signin);
        console.log(response.data.user);
        let token = response.data.accessToken;
        let user = response.data.user;

        localStorage.setItem("jwt", token);
        localStorage.setItem("user", JSON.stringify(user));

        if (token) {
          swal("Welcome!", "Successful signin", "success");
          this.$router.push("/home");
        }
      } catch (e) {
        swal("Oops!", "Something went wrong!", "error");
      }
    },
  },
};
</script>

<style>
  #fondoLogin{
    background-color:wheat;
    background-image: url("../../assets/background.jpg");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment:fixed;
    height: 757px;
    overflow-y: hidden;
  }
  #fondoFormulario{
    background-color: rgba(233, 233, 233, 0.93);
    /* background-color: rgba(232, 240, 254, 0.93); */
    /* background-color: rgb(232, 240, 254); */
    border-radius: 10px;
    /* esto estaba directamente en el template -> style="width: 100%" */
    width: 300px;
  }
</style>
