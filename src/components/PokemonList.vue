<template>

  <div id="pokemon-list">
     <form v-on:submit.prevent>
      <select>
        <option disabled value="">Select a Pokemon...</option>
        <option v-for="(pokemon, index) in pokemon" :pokemon='pokemon' :key="index">
         {{pokemon.name}}
        </option>
      </select>
    </form>
  </div>


</template>

<script>
import SinglePokemon from './SinglePokemon'

export default {
  name: 'pokemon-list',
  props: ['pokemon'],
  components: {
    'single-pokemon': SinglePokemon
  }
}

</script>

<style>

</style>