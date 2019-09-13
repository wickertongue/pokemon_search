<template>

  <div id="pokemon-filter">
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

export default {
  name: 'pokemon-filter',
  props: ['pokemon']
}

</script>

<style>

</style>