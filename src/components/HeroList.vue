<template>
    <div id="HeroList">
        <HeroCard v-for="hero in heroes"
            v-bind:key="hero.id"
            v-bind:hero="hero"/>
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