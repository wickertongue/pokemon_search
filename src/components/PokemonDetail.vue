<template>
  <div>
    <div v-if="pokemon" id="pokemonDetail">
      <h3>{{pokemon.name}}</h3>
        <ul>
          <li>height: {{selectedPokemonDetails.height}}</li>
          <li>weight: {{selectedPokemonDetails.weight}}</li>
          <li>species: {{selectedPokemonDetails.species.name}}</li>
        </ul>
        <h4>elemental types:</h4>
          <ul>
            <li v-for="type in selectedPokemonDetails.types">
              <span v-for="object in type">
                {{object.name}}
              </span>
            </li>
          </ul>
      </div>
      <div id="images">
        <img 
          v-if="selectedPokemonDetails.sprites!==null"
          v-for="image in selectedPokemonDetails.sprites" 
          :src="image" >
      </div>
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
@import url('https://fonts.googleapis.com/css?family=Press+Start+2P&display=swap');

#images {
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
  /* border: 1px solid black; */
}

img {
  /* border: 1px solid black; */
}

#pokemonDetail {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  /* border: 1px solid black; */
}

</style>