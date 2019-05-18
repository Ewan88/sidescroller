<template lang="html">
  <div id="forest">
    <div id="back"
      :class="{'parallax': true,
                'moveLeft': mouse=='left',
                'moveRight': mouse=='right'
              }"
    />
    <div id="lights"
      :class="{'parallax': true,
                'moveLeft': mouse=='left',
                'moveRight': mouse=='right'
              }"
    />
    <div id="mid"
      :class="{'parallax': true,
                'moveLeft': mouse=='left',
                'moveRight': mouse=='right'
              }"
    />
    <div id="front"
      :class="{'parallax': true,
                'moveLeft': mouse=='left',
                'moveRight': mouse=='right'
              }"
    />
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'forest',
  data() {
    return {
      mouse: '',
    }
  },
  mounted() {
    eventBus.$on('mouse-left', () => {
      this.mouse = 'left';
    }),
    eventBus.$on('mouse-right', () => {
      this.mouse = 'right';
    })
  },
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
  background-repeat: repeat-x;
  background-size: auto 100%;
}

.moveLeft {
  background-position-x: 30%;
}

.moveRight {
  background-position-x: -30%;
}

</style>
