<template>
  
  <router-view/>
</template>

<script>
import HomeView from './views/Home/HomeView.vue';

export default {
  name: 'App',
  components: {
    HomeView,
  },
};
</script>


<style>
#app {
  font-family: "Montserrat", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}

body{
  margin: 0;
  padding: 0;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}




</style>
