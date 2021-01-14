<template>
  <div id="app">
  <MealsList/>
  </div>
</template>

<script>
import MealsList from './components/MealsList.vue'

export default {
  name: 'App',
  components: {
    MealsList
  },
  data() {
    return {
    }
  },
  methods:{
    }
  }

</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: auto;
  max-width: 70%;
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
</style>
