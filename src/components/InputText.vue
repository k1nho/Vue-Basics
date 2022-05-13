<script setup>
import { ref } from "vue";

const userMsg = ref("");
</script>

<template>
  <div>
    <h2>Basic Input Example</h2>
    <input v-model="userMsg" placeholder="Write Message and See Change" />
    <p>Message is: {{ userMsg }}</p>
  </div>
</template>
