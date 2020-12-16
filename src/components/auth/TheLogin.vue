<template>
  <div class="container mt-3" style="width: 50%">
    <form>
      <div class="mb-3">
        <label for="exampleInputEmail1" class="form-label">Email address</label>
        <input
          v-model="signin.email"
          type="email"
          class="form-control"
          id="exampleInputEmail1"
          aria-describedby="emailHelp"
        />
        <div id="emailHelp" class="form-text">
          We'll never share your email with anyone else.
        </div>
      </div>
      <div class="mb-3">
        <label for="exampleInputPassword1" class="form-label">Password</label>
        <input
          v-model="signin.password"
          type="password"
          class="form-control"
          id="exampleInputPassword1"
        />
        <pre>
            {{ signin }}
        </pre>
      </div>
      <button @click.prevent="signinUser" type="submit" class="btn btn-primary">
        signin
      </button>
    </form>
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
        console.log(response.data);
        let token = response.data.tokenReturn;
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
</style>