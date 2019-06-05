<template lang="html">
  <div id="player" v-bind:style="{
    backgroundPosition: computedPosition,
    transform: computedRotation
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
      rotation: 0,
    }
  },
  computed: {
    computedPosition: function () {
      return `${this.backgroundX}px ${this.backgroundY}px`;
    },
    computedRotation: function () {
      return `rotate(${this.rotation}deg)`
    },
  },
  methods: {
    rotateAnimation(event){
      let centerX = window.innerWidth / 2;
      let centerY = window.innerHeight / 2;
      let angle = Math.atan2(event.x - centerX,
        -(event.y - centerY)) * (180 / Math.PI);
      this.rotation = Math.floor(angle);
    },

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
    let wrapper = this.$parent.$refs.wrapper;
    this.$parent.addEvent(wrapper, "mousemove", this.rotateAnimation);

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
