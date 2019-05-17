<template lang="html">
  <div ref="wrapper">
    <div id="background" class="parallax"></div>
    <div id="lights" class="parallax"></div>
    <div id="midground" class="parallax"></div>
    <div id="front" class="parallax"></div>
  </div>
</template>

<script>
export default {
  name: 'forest',
}
</script>

<style lang="css" scoped>

#background {
  background-image: url('../assets/forest/background.png');
  z-index: 0;
  transition-duration: 1s;
}

#lights {
  background-image: url('../assets/forest/lights.png');
  z-index: 1;
  transition-duration: 0.8s;
}

#midground {
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
  height: 100%;
  width: 100%;
  background-attachment: local;
  background-position: center;
  background-repeat: repeat-x;
  background-size: auto 70%;
}

.moveLeft {
  background-position-x: 2%;
}

.moveRight {
  background-position-x: -2%;
}



</style>
