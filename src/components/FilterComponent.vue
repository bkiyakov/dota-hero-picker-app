<template>
    <div>
        <span>{{this.label}}</span>
        <input v-for="level in levels" :key="level" type="radio" :name="id" :id="id + `-${level}`" :value="level" @click="uncheckNukeLevel" v-model="currentLevel">
    </div>
</template>

<script>
export default {
    name: "FilterComponent",
    props: ["label", "levels", "id"],
    data() {
        return {
            currentLevel: 0
        }
    },
    methods: {
        uncheckNukeLevel: function(){
            if (this.currentLevel == event.target.value){
                this.currentLevel = 0;
                this.$emit("filterChanged", {id: this.id, currentLevel: 0});
                return;
            }
            this.$emit("filterChanged", {id: this.id, currentLevel: parseInt(event.target.value)});
        }
    }
}
</script>