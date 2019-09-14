<template>

  <div class="mainApp">
    <h1>Pokemon Search!</h1>
      <div>
        <pokemon-filter :pokemon="allPokemon"></pokemon-filter>
        <pokemon-detail 
          :pokemon="selectedPokemon" 
          :selected-pokemon-details="selectedPokemonDetails"></pokemon-detail>
      </div>
  </div>

</template>

<script>
  import PokemonFilter from './components/PokemonFilter'
  import PokemonDetail from './components/PokemonDetail'
  import {eventBus} from './main'

  export default {
      data() {
      return {
        allPokemon: [],
        favouritePokemon: [],
        selectedPokemon: null,
        selectedPokemonDetails: null
      }
    },
    mounted() {
      fetch('https://pokeapi.co/api/v2/pokemon/?limit=2000')
      .then(response => response.json())
      .then(pokemon => this.allPokemon = pokemon.results);

      eventBus.$on('selected-pokemon', (singlePokemon) => {
      this.selectedPokemon = singlePokemon;
      fetch(this.selectedPokemon.url)
      .then(response => response.json())
      .then(pokemon => this.selectedPokemonDetails = pokemon);
      });
    },
    components: {
      'pokemon-filter': PokemonFilter,
      'pokemon-detail': PokemonDetail
    }
  }
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Press+Start+2P&display=swap');

.mainApp {
  margin: 10px;
}

h1 {
  font-family: 'Press Start 2P';
}

</style>
