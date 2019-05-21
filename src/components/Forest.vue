<template lang="html">
  <div id="forest" ref="wrapper">
    <div id="back" class="parallax"
      v-bind:style="{
        backgroundPositionX: computedX,
        backgroundPositionY: computedY
      }"
    />
    <div id="lights" class="parallax"
      v-bind:style="{
        backgroundPositionX: computedX,
        backgroundPositionY: computedY
      }"
    />
    <div id="mid" class="parallax"
      v-bind:style="{
        backgroundPositionX: computedX,
        backgroundPositionY: computedY
      }"
    />
    <div id="front" class="parallax"
      v-bind:style="{
        backgroundPositionX: computedX,
        backgroundPositionY: computedY
      }"
    />
  </div>
</template>

<script>
// import { eventBus } from '../main.js';

export default {
  name: 'forest',
  data() {
    return {
      mouseX: null,
      mouseY: null,
    }
  },
  computed: {
    computedX: function () {
      return this.mouseX;
    },
    computedY: function () {
      return this.mouseY;
    }
  },
  methods: {
    addEvent(target, event, listener) {
      if (target.addEventListener) {
        target.addEventListener(event, listener);
      }
    },

    mouseMove(event) {
      let windowX = window.innerWidth;
      let windowY = window.innerHeight;
      let x = event.pageX;
      let y = event.pageY;
      let newX = windowX - x;
      let newY = windowY - y;
      console.log('window: ' + windowX + ', ' + windowY + ' mouse: ' + x + ', ' + y + ' new: ' + newX + ', ' + newY);

      this.mouseX = newX + 'px';
      this.mouseY = newY + 'px';
    }
  },
  mounted() {
    let wrapper = this.$refs.wrapper;
    console.log(this);
    this.addEvent(wrapper, "mousemove", this.mouseMove);
  }
}
</script>

<style lang="css" scoped>

#forest {
  margin-top: 100px;
  height: 400px;
  width: auto;
}

#back {
  background-image: url('../assets/forest/background.png');
  z-index: 0;
  transition-duration: 1s;
}

#lights {
  background-image: url('../assets/forest/lights.png');
  z-index: 1;
  transition-duration: 0.8s;
}

#mid {
  background-image: url('../assets/forest/midground.png');
  z-index: 2;
  transition-duration: 0.6s;
}

#front {
  background-image: url('../assets/forest/foreground.png');
  z-index: 3;
  transition-duration: 0.4s;
}

.parallax {
  position: fixed;
  height: 400px;
  width: 100%;
  background-attachment: local;
  background-position: center;
  background-repeat: repeat;
  background-size: auto 110%;
}

.moveLeft {
  background-position-x: 30%;
}

.moveRight {
  background-position-x: -30%;
}

</style>
