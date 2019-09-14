<template>

  <div v-if="pokemon" id="pokemonDetail">
    <h3>Name: {{pokemon.name}}</h3>
      <ul>
        <li>Base Experience: {{selectedPokemonDetails.base_experience}}</li>
        <li>Height: {{selectedPokemonDetails.height}}</li>
        <li>Weight: {{selectedPokemonDetails.weight}}</li>
        <li>Species: {{selectedPokemonDetails.species.name}}</li>
      </ul>
        <div>
          <h4>Types:</h4>
            <ul>
              <li v-for="type in selectedPokemonDetails.types">
                <span v-for="object in type">
                  {{object.name}}
                </span>
              </li>
            </ul>
        </div>
    <div class="images">
      <img 
        v-if="selectedPokemonDetails.sprites!==null"
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