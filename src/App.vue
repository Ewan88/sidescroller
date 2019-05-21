<template>
  <div id="app">
    <Forest/>
  </div>
</template>

<script>
import Forest from './components/Forest.vue'
// import { eventBus } from './main.js';

export default {
  name: 'app',
  components: {
    Forest
  },
}
</script>

<style>

body {
  margin: 0;
  background-color: black;
  text-align: center;
  color: white;
}

#app {
  height: 100%;
  width: auto;
}

</style>
