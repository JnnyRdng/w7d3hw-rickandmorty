<template>
  <div>
    <h1>Rick and Morty</h1>
    <div>
      <label for="search-box">Search:</label>
      <input
        type="text"
        list="character-list"
        id="search-box"
        v-model="filterString"
        v-on:input="filterByString"
      />
      <!-- <datalist id="character-list">
        <option v-for="(character, index) in characters" :key="index">{{character.name}}</option>
      </datalist>-->
      <!-- <input type="submit" value="Search" /> -->
      <p>Filtered:{{filterLength}}</p>
    </div>
    <main>
      <character-list :characters="characters"></character-list>
      <character-detail v-if="searchCharacter" :character="searchCharacter"></character-detail>
      <character-detail v-else :character="selectedCharacter"></character-detail>
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
      filterString: "",
      filteredCharacters: [],
      searchCharacter: null,
    };
  },
  mounted() {
    fetch("https://rickandmortyapi.com/api/character/")
      .then((response) => response.json())
      .then((characters) => (this.characters = characters.results));

    eventBus.$on("character-selected", (character) => {
      this.selectedCharacter = character;
    });

    eventBus.$on("clear-search", (res) => {
      this.filterString = "";
      this.searchCharacter = null;
    });
  },
  components: {
    "character-list": CharacterList,
    "character-detail": CharacterDetail,
  },
  methods: {
    filterByString: function () {
      this.filteredCharacters = this.characters.filter((character) => {
        return (
          character.name
            .toLowerCase()
            .indexOf(this.filterString.toLowerCase()) > -1
        );
      });
      // this.filterString = "";
      if (this.filteredCharacters.length === 1) {
        this.searchCharacter = this.filteredCharacters[0];
      } else {
        this.searchCharacter = null;
      }
      // return this.searchCharacter;
    },
  },
  computed: {
    filterLength: function () {
      return this.filteredCharacters.length;
    },
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