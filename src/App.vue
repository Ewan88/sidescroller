<template>
  <div id="app">
    <Forest/>
  </div>
</template>

<script>
import Forest from './components/Forest.vue'

export default {
  name: 'app',
  components: {
    Forest
  }
}
</script>

<style>

body {
  margin: 0;
}

#app {
  
}

div {
  display: flex;
  flex-direction: column;
}

</style>
