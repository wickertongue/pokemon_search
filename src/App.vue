<template>
  <div>
    <p>Name: {{allPokemon[0].name}}</p>
    <p>URL: {{allPokemon[0].url}}</p>
  </div>
</template>

<script>
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
    }
  }
</script>

<style>

</style>


