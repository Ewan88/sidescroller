<template lang="html">
  <div id="forest">
    <div id="back"
      :class="{'parallax': true,
                'moveLeft': movingLeft,
                'moveRight': movingRight
              }"
    />
    <div id="lights"
      :class="{'parallax': true,
                'moveLeft': movingLeft,
                'moveRight': movingRight
              }"
    />
    <div id="mid"
      :class="{'parallax': true,
                'moveLeft': movingLeft,
                'moveRight': movingRight
              }"
    />
    <div id="front"
      :class="{'parallax': true,
                'moveLeft': movingLeft,
                'moveRight': movingRight
              }"
    />
  </div>
</template>

<script>
export default {
  name: 'forest',
  data() {
    return {
      movingLeft: false,
      movingRight: false
    }
  },
  mounted() {

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
  background-position-x: 2%;
}

.moveRight {
  background-position-x: -2%;
}

</style>
