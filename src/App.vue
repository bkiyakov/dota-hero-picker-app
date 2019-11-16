<template>
  <div id="main">
    <HeroCard name="Mirana" img="https://gamepedia.cursecdn.com/dota2_gamepedia/1/12/Mirana_icon.png"/>
    <HeroCard name="Ember Spirit" img="https://liquipedia.net/commons/images/9/98/Ember_Spirit_Large.png"/>
    <HeroCard name="Monkey King" img="https://gamepedia.cursecdn.com/dota2_gamepedia/7/7b/Monkey_King_icon.png"/>
  </div>
</template>

<script>
import HeroCard from './components/HeroCard.vue'

export default {
  name: 'app',
  components: {
    HeroCard
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

#main {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}
</style>
