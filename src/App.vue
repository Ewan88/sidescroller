<template>
  <div id="app">
    <Game/>
  </div>
</template>

<script>
import Game from './components/Game.vue'
// import { eventBus } from './main.js';

export default {
  name: 'app',
  components: {
    Game
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
