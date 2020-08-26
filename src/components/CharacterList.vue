<template>
  <div>
      <ul>
          <list-item v-for="(character, index) in characters" :key="index" :character="character"></list-item>
        </ul>
  </div>
</template>

<script>
import ListItem from "./ListItem.vue";

export default {
    name: 'character-list',
    props: ['characters'],
    components:{
        "list-item": ListItem
    }

}
</script>

<style>

</style>