<template>

  <div class="main app">
    <h1>Pokemon Search!</h1>
      <div>
        <pokemon-filter :pokemon="allPokemon"></pokemon-filter>

      </div>
  </div>

</template>

<script>
  import PokemonFilter from './components/PokemonFilter'
  import {eventBus} from './main'

  export default {
      data() {
      return {
        allPokemon: [],
        favouritePokemon: [],
        selectedPokemon: null
      }
    },
    mounted() {
      fetch('https://pokeapi.co/api/v2/pokemon/?limit=2000')
      .then(response => response.json())
      .then(pokemon => this.allPokemon = pokemon.results)

      eventBus.$on('selected-pokemon', (singlePokemon) => {
      this.selectedPokemon = singlePokemon;
      })
    },
    components: {
      'pokemon-filter': PokemonFilter
    }
  }
</script>

<style>

</style>


