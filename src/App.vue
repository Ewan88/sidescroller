<template>
  <div id="app">
    <div id="container">
      <p>This is the container</p>
      <div id="wrapper" ref="wrapper">
        <Forest/>
      </div>
    </div>
  </div>
</template>

<script>
import Forest from './components/Forest.vue'

import { eventBus } from './main.js';

export default {
  name: 'app',
  components: {
    Forest
  },
  methods: {
    addEvent(target, event, listener) {
      if (target.addEventListener) {
        target.addEventListener(event, listener);
      }
    },
  },
  mounted() {
    let wrapper = this.$refs.wrapper;
    this.addEvent(wrapper, "mousemove", this.mouseMove);
  }
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
