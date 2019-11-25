<template>
  <div id="main">
    <input id="searchbar" type="text" placeholder="Type for search hero..." v-model="searchfield">
    <div id="filters">
      <div>
        <input type="radio" name="rangeFilter" id="melee" @click="uncheckRange" value="Melee" v-model="rangeFilter">
        <label for="melee">Melee</label>
        <input type="radio" name="rangeFilter" id="ranged" @click="uncheckRange" value="Ranged" v-model="rangeFilter">
        <label for="ranged">Range</label>
      </div>
      <FilterComponent v-for="nukeLevel in nukeLevels"
        :key="nukeLevel.id"
        :id="nukeLevel.id"
        :label="nukeLevel.label"
        :levels="nukeLevel.levels"
        @filterChanged="changeNukeFilter($event.id, $event.currentLevel)"/>
    </div>
    <HeroList
      v-bind:heroes="filtered_heroes"/>
  </div>
</template>

<script>

import HeroList from './components/HeroList.vue';
import FilterComponent from './components/FilterComponent.vue';
const heroes = require("./data/heroes.json");
const nukeLevels = require("./data/nukelevels.json");

export default {
  name: 'app',
  components: {
    HeroList,
    FilterComponent
  },
  data(){
    return{
      heroes: heroes,
      searchfield: '',
      rangeFilter: '',
      nukeLevels: nukeLevels,
      nukeLevelsFilter: []
    }
  },
  computed: {
    filtered_heroes: function(){
        return this.heroes.filter(hero =>
          hero.localized_name.toLowerCase().includes(this.searchfield.toLowerCase()) &&
          hero.attack_type.includes(this.rangeFilter) &&
          this.checkNukeFilter(hero.nuke_levels)
        )
    }
  },
  methods: {
    uncheckRange: function(){
      if (this.rangeFilter != '' && this.rangeFilter == event.target.value){
        this.rangeFilter = '';
      }
    },
    changeNukeFilter: function(nukeId, nukeLevel){
      this.nukeLevelsFilter.forEach(nuke => {
        if(nuke.hasOwnProperty(nukeId)){
          nuke[nukeId] = nukeLevel;
        }
      })
    },
    checkNukeFilter: function(heroNukesObj){
      let heroMatched = true;
      //Может надо просто заменить сравнением двух массивов
      Object.keys(heroNukesObj).forEach(nukeId => {
        this.nukeLevelsFilter.forEach(nukeObj => {
          if (nukeObj.hasOwnProperty(nukeId) && nukeObj[nukeId] > heroNukesObj[nukeId]){
            heroMatched = false;
          }
        })
      })
      return heroMatched;
    }
  },
  created(){
    nukeLevels.map(nukeLevel => {
      this.nukeLevelsFilter.push({
        [nukeLevel.id]: 0
      })
    })
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

#searchbar {
  width: 80%;
  height: 30px;
  font-size: 15px;
  margin: 5px 10% 5px 10%;
}

</style>
