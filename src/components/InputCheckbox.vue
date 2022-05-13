<script setup>
import { ref } from "vue";
const checkedNames = ref([]);
</script>

<template>
  <div>
    <h2>Basic Checkbox Example</h2>
    <input type="checkbox" id="kin" value="Kin" v-model="checkedNames" />
    <label for="kin">Kin</label>
    <input
      type="checkbox"
      id="pikachu"
      value="Pikachu"
      v-model="checkedNames"
    />
    <label for="pikachu">Pikachu</label>
    <input type="checkbox" id="rose" value="Rose" v-model="checkedNames" />
    <label for="rose">Rose</label>
    <p>Selected Names : {{ checkedNames }}</p>
  </div>
</template>
