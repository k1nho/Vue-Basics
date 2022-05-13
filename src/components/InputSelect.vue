<script setup>
import { ref } from "vue";
const selectedPokemon = ref("");
const options = ref([
  { text: "Infernape", value: "Infernape" },
  { text: "Floatzel", value: "Floatzel" },
  { text: "Torterra", value: "Torterra" },
]);
</script>

<template>
  <div>
    <h2>Basic Select Example</h2>
    <select v-model="selectedPokemon">
      <option disabled value="">Select a Value</option>
      <option v-for="pokemon in options" :value="pokemon.value">
        {{ pokemon.text }}
      </option>
    </select>
    <p>I choose you! {{ selectedPokemon }}</p>
  </div>
</template>
