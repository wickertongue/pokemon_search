<template>

  <div id="pokemon-filter">
     <form v-on:submit.prevent>
      <select v-on:change="handleSelect" v-model="selectedPokemon">
        <option disabled value="">Select a Pokemon...</option>
        <option v-for="(pokemon, index) in pokemon" :pokemon='pokemon' :key="index">
         {{pokemon.name}}
        </option>
      </select>
    </form>
  </div>


</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'pokemon-filter',
  data(){
    return {
      "selectedPokemon": {}
    }
  },
  props: ['pokemon'],
  methods: {
    handleSelect() {
    eventBus.$emit('selected-pokemon', this.selectedPokemon)
    }
  }
  
}

</script>

<style>

</style>