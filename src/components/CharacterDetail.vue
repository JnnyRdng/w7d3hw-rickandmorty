<template>
  <div v-if="character">
    <img :src="character.image" alt />
    <h4>{{character.name}}</h4>
    <p>Species: {{character.species}}</p>
    <p>Gender: {{character.gender}}</p>
    <p>Origin: {{character.origin.name}}</p>
    <p>Location: {{character.location.name}}</p>
    <p>Status: {{character.status}}</p>
  </div>
</template>

<script>
export default {
  name: "character-detail",
  props: ["character"],
};
</script>

<style scoped>
div {
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  margin-right: 100px;
}
img {
  margin: 10px;
}
</style>