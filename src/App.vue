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
    <div id="bounding-box" />
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

    keyListener(event) {
      console.log(event.key);
      switch (event.key) {
        case "w":
          this.moveBackground(0, 100);
          break;
        case "a":
          this.moveBackground(100, 0);
          break;
        case "s":
          this.moveBackground(0, -100);
          break;
        case "d":
          this.moveBackground(-100, 0);
          break;
      }
      eventBus.$emit('player-move');
    },

    moveBackground(x, y) {
      this.backgroundX += x
      this.backgroundY += y
    },

    // mouseListener(event) {
    //   let x = -(event.offsetX - (window.innerWidth / 2));
    //   let y = -(event.offsetY - (window.innerHeight / 2));
    //   this.moveBackground(x, y)
    //   eventBus.$emit('player-move');
    // },

  },
  mounted() {
    let wrapper = this.$refs.wrapper;
    this.addEvent(wrapper, "mousedown", this.mouseListener);
    this.addEvent(window, "keydown", this.keyListener);
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
  cursor: url('./assets/crosshair.png'), crosshair;
}

#back {
  background-image: url('./assets/background/stars_back.png');
  z-index: 0;
  transition-duration: 1s;
}

#mid {
  background-image: url('./assets/background/stars_mid.png');
  z-index: 1;
  transition-duration: 0.7s;
}

#front {
  background-image: url('./assets/background/stars_front.png');
  z-index: 2;
  transition-duration: 0.5s;
}

#dust {
  background-image: url('./assets/background/dust.png');
  z-index: 3;
  transition-duration: 0.3s;
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
