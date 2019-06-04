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
      moving: false,
    }
  },
  computed: {
    computedPos: function () {
      return `${this.backgroundX}px ${this.backgroundY}px`;
    },
  },
  methods: {
    moveAnimation(){
      this.backgroundY += 100;
      if (this.moving) {
        setTimeout(() => {
          this.moveAnimation();
        }, 400)
      } else {
        this.backgroundY = 0;
      }
    },
  },
  mounted() {
    eventBus.$on('player-move', () => {
      this.moving = true;
      this.moveAnimation();
      setTimeout(() => {
        this.moving = false;
      }, 1200);
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
   background-repeat: repeat;
 }

</style>
