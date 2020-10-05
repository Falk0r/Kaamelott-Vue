<template>
  <v-container
    class="parallax"
    :style="'background-image: url(' + image + ');'"
  >
  </v-container>
</template>

<script>
  export default {
    name: 'Parallax',
    props : ['image']
  }
</script>

<style lang="less" scoped>
  .parallax {
      background-attachment: fixed;
      background-position: center;
      background-repeat: no-repeat;
      background-size: cover;
      height: 80vh;
      max-width: 100%;
  }
</style>
