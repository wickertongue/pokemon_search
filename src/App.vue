<template>

  <div class="main app">
    <h1>Pokemon Search!</h1>
      <div>
        <pokemon-list :pokemon="allPokemon"></pokemon-list>

      </div>
  </div>

</template>

<script>
  import PokemonList from './components/PokemonList'

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
    },
    components: {
      'pokemon-list': PokemonList
    }
  }
</script>

<style>

</style>


