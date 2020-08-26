<template>
  <div>
      <!-- <ul> -->
          <label for="character-select">Select a character</label>
          <select v-on:change="mouseClick" v-model="selected" id="character-select">
              <option disabled > Choose a character</option>
              <list-option v-for="(character, index) in characters" :key="index" :index="index" :character="character"></list-option>
          </select>

          <!-- <list-item v-for="(character, index) in characters" :key="index" :character="character"></list-item> -->
        <!-- </ul> -->
  </div>
</template>

<script>
import { eventBus } from '../main.js'
// import ListItem from "./ListItem.vue";
import ListOption from "./ListOption.vue";

export default {
    name: 'character-list',
    data() {
        return {
            selected: null
        }
    },
    props: ['characters'],
    components:{
        // "list-item": ListItem,
        "list-option": ListOption
    },
    methods: {
        mouseClick(){
            eventBus.$emit('character-selected', this.characters[this.selected-1])
        }
    }
}
</script>

<style>

</style>