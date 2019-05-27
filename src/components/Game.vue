<template lang="html">
  <div id="wrapper" ref="wrapper">
    <div id="back" class="parallax" v-bind:style="{
      backgroundPositionX: computedX,
      backgroundPositionY: computedY
      }">
    </div>
    <div id="mid" class="parallax" v-bind:style="{
      backgroundPositionX: computedX,
      backgroundPositionY: computedY
      }">
    </div>
    <div id="front" class="parallax" v-bind:style="{
      backgroundPositionX: computedX,
      backgroundPositionY: computedY
      }">
    </div>
  </div>
</template>

<script>
// import { eventBus } from '../main.js';

export default {
  name: 'game',
  data() {
    return {
      backgroundX: null,
      backgroundY: null,
    }
  },
  computed: {
    computedX: function () {
      return this.backgroundX + 'px';
    },
    computedY: function () {
      return this.backgroundY + 'px';
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
      // let newX = x - (windowX / 2);
      // let newY = y - (windowY / 2);

      this.backgroundX = (windowX - x);
      this.backgroundY = (windowY - y);

      /*
      if mouse is in center:
        set bg position to mouse position
      otherwise:
        add mouse position to bg position
      */

      // if (this.backgroundX == null || this.backgroundY == null) {
      //   this.backgroundX = (windowX - x);
      //   this.backgroundY = (windowY - y);
      //   return;
      // } else if ((newX > -10 && newX < 10) || (newY > -10 && newY < 10)) {
      //   this.backgroundX = (windowX - x);
      //   this.backgroundY = (windowY - y);
      //   return;
      // } else {
      //   this.backgroundX += (windowX - x) / 2;
      //   this.backgroundY += (windowY - y) / 2;
      //   return;
      // }
    }
  },
  mounted() {
    let wrapper = this.$refs.wrapper;
    this.addEvent(wrapper, "mousemove", this.mouseMove);
  }
}
</script>

<style lang="css" scoped>

#space {
  height: 100%;
  width: auto;
}

#back {
  background-image: url('../assets/background/stars_back.png');
  z-index: 0;
  transition-duration: 0.5s;
}

#mid {
  background-image: url('../assets/background/stars_mid.png');
  z-index: 2;
  transition-duration: 1s;
}

#front {
  background-image: url('../assets/background/stars_front.png');
  z-index: 3;
  transition-duration: 2s;
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
