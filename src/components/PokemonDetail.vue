<template>
  <div v-if="pokemon" id="pokemonDetail">
    <p>Name: {{pokemon.name}}</p>
    <p>Link to Detail: {{pokemon.url}}</p>


  </div>
  
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'pokemon-detail',
  props: ['pokemon']
}
</script>

<style>

</style>