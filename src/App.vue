<template>
  <div id="app" ref="wrapper">
    <div id="back" class="parallax" v-bind:style="{
      backgroundPosition: computedPos,
      }">
    </div>
    <div id="mid" class="parallax" v-bind:style="{
      backgroundPosition: computedPos,
      }">
    </div>
    <div id="front" class="parallax" v-bind:style="{
      backgroundPosition: computedPos,
      }">
    </div>
    <div id="dust" class="parallax" v-bind:style="{
      backgroundPosition: computedPos,
      }">
    </div>
    <Player/>
  </div>
</template>

<script>
import { eventBus } from './main.js';
import Player from './components/Player.vue';

export default {
  name: 'app',
  components: {
    "Player": Player
  },
  data() {
    return {
      backgroundX: 0,
      backgroundY: 0,
    }
  },
  computed: {
    computedPos: function () {
      return `${this.backgroundX}px ${this.backgroundY}px`;
    },
  },
  methods: {
    addEvent(target, event, listener) {
      if (target.addEventListener) {
        target.addEventListener(event, listener);
      }
    },

    mouseListener(event) {
      let windowX = window.innerWidth;
      let windowY = window.innerHeight;
      let x = event.offsetX;
      let y = event.offsetY;

      // let newX = x - (windowX / 2);
      // let newY = y - (windowY / 2);

      this.backgroundX += -(x - (windowX / 2));
      this.backgroundY += -(y - (windowY / 2));

      eventBus.$emit('player-move', x, y);
    },
  },
  mounted() {
    let wrapper = this.$refs.wrapper;
    this.addEvent(wrapper, "mousedown", this.mouseListener);
  }
}
</script>

<style>

body {
  margin: 0;
  background: black;
  text-align: center;
  color: white;
}

#app {
  height: 100%;
  width: 100%;
}

#app:hover {
  cursor: crosshair;
}

#back {
  background-image: url('./assets/background/stars_back.png');
  z-index: 0;
  transition-duration: 2s;
}

#mid {
  background-image: url('./assets/background/stars_mid.png');
  z-index: 1;
  transition-duration: 1.8s;
}

#front {
  background-image: url('./assets/background/stars_front.png');
  z-index: 2;
  transition-duration: 1.6s;
}

#dust {
  background-image: url('./assets/background/dust.png');
  z-index: 3;
  transition-duration: 1.4s;
}

.parallax {
  position: fixed;
  height: 100%;
  width: 100%;
  background-attachment: local;
  background-position: center;
  background-repeat: repeat;
  background-size: auto;
}

</style>
