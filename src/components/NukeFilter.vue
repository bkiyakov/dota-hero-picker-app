<template>
    <div class="filter-nuke">
        <span>{{filterName}}</span>
        <input type="radio" name="nukeName" :id="name + '_1'" @click="uncheckRange" value="1" v-model="nukeValue">
        <input type="radio" name="nukeName" :id="name + '_2'" @click="uncheckRange" value="2" v-model="nukeValue">
        <input type="radio" name="nukeName" :id="name + '_3'" @click="uncheckRange" value="3" v-model="nukeValue">
    </div>
</template>

<script>
export default {
    name: "NukeFilter",
    pros: ["filterName"],
    data(){
        return {
            nukeValue: '',
            name: this.filterName
        }
    }
}
</script>