<template>
<div>
    <li v-on:click="mouseClick">{{character.name}} </li>
</div>
  
</template>

<script>
import { eventBus } from '../main.js'
export default {
    name: 'list-item',
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