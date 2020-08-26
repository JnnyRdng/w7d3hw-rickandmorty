<template></template>

<script>
import { eventBus } from "./main.js";
import CharacterList from "./components/CharacterList.vue";
import CharacterDetail from "./components/CharacterDetail.vue";

export default {
  name: "App",
  data() {
    return {
      characters: [],
      selectedCharacter: null,
    };
  },
  mounted() {
    fetch("https://rickandmortyapi.com/api/character/")
      .then((response) => response.json())
      .then((characters) => (this.characters = characters));

    eventBus.$on("character-selected", (character) => {
      this.selectedCharacter = character;
    });
  },
  components: {
    "character-list": CharacterList,
    "character-detail": CharacterDetail,
  },
};
</script>

<style>
</style>