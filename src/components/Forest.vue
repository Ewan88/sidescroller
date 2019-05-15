<template lang="html">
  <div id="forest">
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
}

#lights {
  background-image: url('../assets/forest/lights.png');
  z-index: 1;
}

#midground {
  background-image: url('../assets/forest/midground.png');
  z-index: 2;
}

#front {
  background-image: url('../assets/forest/foreground.png');
  z-index: 3;
}

.parallax {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  height: 100%;
  width: 100%;
  background-attachment: local, scroll;
  background-position: center;
  background-repeat: repeat-x;
  background-size: 100%;
}

</style>
