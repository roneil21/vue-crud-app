<template>
  <TodoHeader />
  <RouterView />
</template>

<script setup>
import { RouterView } from "vue-router"
import TodoHeader from "./components/TodoHeader.vue"
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;700&family=Poppins:wght@300;400;500;600&display=swap');

* {
  font-family: "Open Sans", sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}
</style>