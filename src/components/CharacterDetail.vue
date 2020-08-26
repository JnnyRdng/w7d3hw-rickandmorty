<template>
  <div>
      <img :src="character.image" alt="">
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
    name: 'character-detail',
    props: ['character']

}
</script>

<style>

</style>