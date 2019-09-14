<template>

  <div id="pokemon-filter">
    <div>
      <form>
      <input type="text" v-model="searchedPokemon" placeholder="search for a Pokemon..." v-on:keyup="searchForPokemon">
      </form>
    </div>

    <div>
      <select v-on:change="handleSelect" v-model="selectedPokemon">
        <option disabled value="">Select a Pokemon...</option>
        <option v-for="(pokemon, index) in pokemon" :pokemon='pokemon' :key="index" :value="pokemon">
         {{pokemon.name}}
        </option>
      </select>
    </div>
  </div>

</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'pokemon-filter',

  data(){
    return {
      "selectedPokemon": "",
      "searchedPokemon": "",
      "pokemonDetails" : null
    }
  },
  props: ['pokemon'],
  methods: {
    handleSelect() {
      this.searchedPokemon = "";
      eventBus.$emit('selected-pokemon', this.selectedPokemon)
    },
    searchForPokemon(){
      let foundPokemon = this.pokemon.find((pokemon) => {
        return pokemon.name.toLowerCase().indexOf(this.searchedPokemon.toLowerCase()) > -1
      })
      this.selectedPokemon = foundPokemon

      eventBus.$emit('selected-pokemon', this.selectedPokemon)
    }
  }
}

</script>

<style scoped>

div {
  border: 1px solid black;
}

</style>