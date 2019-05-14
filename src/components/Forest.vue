<template lang="html">
  <div id="background">
    <img id="back"
      src="../assets/forest/backTrees.png"
    />
    <img id="lights"
      src="../assets/forest/lights.png"
    />
    <img id="middle"
      src="../assets/forest/middleTrees.png"
    />
    <img id="front"
      src="../assets/forest/frontTrees.png"
    />
  </div>
</template>

<script>
export default {
  name: 'forest',
}
</script>

<style lang="css" scoped>

  img {
    position: absolute;
    height: 100%;
    width: 100%;
  }

</style>
