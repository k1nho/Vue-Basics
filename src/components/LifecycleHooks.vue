<script setup>
import { onMounted } from "vue";

onMounted(() => {
  console.log("LifecyleHooks.vue was mounted!");
});
</script>

<template>
  <div>
    Each component instance has a series of steps it follows to initialize and
    run. Along the way it runs functions called lifecycle hooks which give us
    the opportunity to add code to certain parts of the process.
  </div>
</template>
