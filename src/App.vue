<template>

    <div id="app">
      <!-- <div id="nav">
        <router-link to="/">Login</router-link> |
        <router-link to="/Home">Home</router-link>
      </div> -->
      <router-view />
    </div>

</template>

<style>
#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif; */
  font-family:-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: auto;
  
}

/* #fondo{
  background-image: url("./assets/background.jpg");
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  background-attachment:fixed;
  height: 800px;
} */

/* #nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
} */
</style>
