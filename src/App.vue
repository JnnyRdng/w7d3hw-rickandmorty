<template>
    <div>
        <h1>Rick and Morty</h1>
        <main>
        <character-list :characters="characters"></character-list>
        <character-detail :character="selectedCharacter"></character-detail>
        </main>
    </div>
</template>

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
      .then((characters) => (this.characters = characters.results));

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
main {
    display: flex;
    flex-flow: row wrap;
    justify-content: space-between;
}
</style>