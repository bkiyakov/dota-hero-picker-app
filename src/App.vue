<template>
  <div id="main">
    <HeroList v-bind:heroes="heroes"/>
  </div>
</template>

<script>

import HeroList from './components/HeroList.vue';
const heroes = require("./data/heroes.json");

export default {
  name: 'app',
  components: {
    HeroList
  },
  data(){
    return{
      heroes: heroes
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


</style>
