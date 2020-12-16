<template>

  <!-- <div id="login" class="d-flex align-items-center justify-content-center"> -->

    <div id="contenedor" class="text-center p-4">

      <h3 class="p-3">Inicio de sesion</h3>

      <div class="md-form form-group w-90 ml-4 mr-4">
        <div class="input-group">
          <i class="fa fa-user prefix"></i>
          <input
            v-model="login.email"
            type="email"
            class="form-control" 
            id="exampleInputEmail1"
            aria-describedby="emailHelp"
            placeholder="Ingrese su correo"
          >
        </div>
      </div>

      <div class="md-form form-group w-90 ml-4 mr-4">
        <div class="input-group">
          <i class="fa fa-key prefix"></i>
          <input
            v-model="login.password"
            type="password"
            class="form-control"
            id="exampleInputPassword1"
            placeholder="Ingrese su contraseña"
          >
        </div>
      </div>
      
      <div class="p-3">
        <button 
        @click.prevent ="LoginUser"
        type="submit" 
        class="btn btn-dark btn-block active"
        >Ingresar</button>
      </div>

    </div>

  <!-- </div> -->

</template>

<script>
export default {
  name: "elogin",
  data() {
    return{
        login:{
            email:'',
            password: ''
        }
    };
  },
  methods: {

      async LoginUser(){
          try{
            let response = await this.$http.post('/api/usuario/login', this.login)
            console.log(response.data);
            let token = response.data.tokenReturn;
            let user = response.data.user;

            localStorage.setItem('jwt', token)
            localStorage.setItem('user',JSON.stringify(user));
            if(token){
                this.$router.push('/home')
            }
            else{
                console.log(err.response)
            }
          }
          catch{}
      }
  }
};
</script>
<style scoped>

/* #login {
  background-image: url("../../background.jpg");
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  background-attachment:scroll;


  width: 1600px;
  height: 659px;

  width: 800px;
  height: 800px;
} */

#contenedor {
  background-color: rgba(232, 240, 254, 0.97);
  /* background-color: rgb(232, 240, 254); */
  border-radius: 10px;

  margin-top:100%;
  margin-bottom:100%;
  /* margin-right:100%; */
  /* margin-left:100%; */


  /* width: 300px;
  height: 300px; */
}

</style>