<script setup>
import { ref } from "vue";

const binary = ref("one");
</script>

<template>
  <h2>Basic Radio Example</h2>
  <input type="radio" id="0" value="zero" v-model="binary" />
  <label for="0" style="margin-right: 10px">Zero</label>
  <input type="radio" id="1" value="one" v-model="binary" />
  <label for="1">One</label>
  <p>Binary is: {{ binary }}</p>
</template>
