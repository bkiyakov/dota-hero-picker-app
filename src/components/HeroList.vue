<template>
    <div id="HeroList">
        <div v-bind:key="hero.id" v-for="hero in heroes">
            <HeroCard v-bind:hero="hero"/>
        </div>
    </div>
</template>

<script>

import HeroCard from './HeroCard.vue';


export default {
    name: "HeroList",
    components: {
        HeroCard
    },
    props: ["heroes"]
}
</script>
<style scoped>
#HeroList {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}
</style>