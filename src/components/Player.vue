<template lang="html">
  <div id="player" v-bind:style="{
    backgroundPosition: computedPos
    }">
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'player',
  data() {
    return {
      backgroundX: 0,
      backgroundY: 0,
    }
  },
  computed: {
    computedPos: function () {
      return `${this.backgroundX}px ${this.backgroundY}`;
    },
  },
  methods: {
    movePlayer(x, y){
      this.backgroundX = 100;
      setTimeout(() => {
        this.backgroundX = 0;
      }, 1400)
    },
  },
  mounted() {
    eventBus.$on('player-move', (positionX, positionY) => {
      this.movePlayer(positionX, positionY);
    });
  }
}
</script>

<style lang="css" scoped>

 #player {
   position: fixed;
   top: 40%;
   left: 45%;
   height: 100px;
   width: 100px;
   background-image: url('../assets/player/player.png');
   z-index: 5;
 }

</style>
