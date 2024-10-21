<script setup>
  import ProgressSpinner from "primevue/progressspinner";
</script>

<template>
  <main>
    <ProgressSpinner style="width: 175px; height: 175px" strokeWidth="3"/>
  </main>
</template>

<style scoped>
  main {
    display: flex;
    align-items: center;
    background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75));
    height: 100%;
  }
</style>