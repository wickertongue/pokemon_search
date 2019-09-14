<template>

  <div v-if="pokemon" id="pokemonDetail">
    <p>Name: {{pokemon.name}}</p>
    <p>Link to Detail: {{pokemon.url}}</p>
    <p>Base Experience: {{selectedPokemonDetails.base_experience}}</p>
    <div class="images">
      <img
      v-if="selectedPokemonDetails.sprites"
      v-for="image in selectedPokemonDetails.sprites"
      :src="image" alt="image of pokemon">
    </div>
  </div>
  
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'pokemon-detail',
  props: ['pokemon', 'selectedPokemonDetails']
}
</script>

<style scoped>

div.images {
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
}

img {
  border: 1px solid black;
}

</style>