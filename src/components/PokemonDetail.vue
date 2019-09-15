<template>
  <div>
    <div v-if="pokemon" id="pokemonDetail">
      <h3>{{pokemon.name}}</h3>
        <table>
          <tr>  
            <th>Height</th>
            <td>{{selectedPokemonDetails.height}} decimeters</td>
          </tr>
          <tr>
            <th>Weight</th>
            <td>{{selectedPokemonDetails.weight}} hectograms</td>
          </tr>
          <tr>
            <th>Species</th>
            <td>{{selectedPokemonDetails.species.name}}</td>
          </tr>
        </table>
        <h4>elemental types:</h4>

          
          <table>
            <tr>
              <td v-for="type in selectedPokemonDetails.types">
                <span v-for="object in type">
                  {{object.name}}
                </span>
              </td>
            </tr>
          </table>
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

table, th, td {
  border-collapse: collapse;
  border: 3px solid #2a75bb;
}

th, td {
  border-bottom: 1px solid grey;
  padding: 15px;
  text-align: left;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}

tr:nth-child(odd) {
  background-color: ivory;
}

tr:hover {
  background-color: #f5ebbc;
}

</style>