<template>
  <div id="app" class="d-flex align-items-center justify-content-center">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
    </div> -->
    
    <router-view :key='$router.name'/>
    
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

#app {
  background-image: url("./background.jpg");
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  background-attachment:fixed;


  /* width: 1600px;
  height: 659px; */

  /* width: 800px; */
  height:auto;
}

</style>
