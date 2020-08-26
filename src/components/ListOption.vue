<template>

    <option :value="character.id">{{character.name}} </option>
  
</template>

<script>
import { eventBus } from '../main.js'
export default {
    name: 'list-option',
    props: ['character'],
    methods: {
        mouseClick(){
            eventBus.$emit('character-selected', this.character)
        }
    }

}
</script>

<style>

</style>