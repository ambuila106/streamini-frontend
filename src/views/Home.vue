<template>
  <div class="home">
    <CoverRandomMedia />
    <MediaBoard />
  </div>
</template>

<script>
import CoverRandomMedia from '../components/CoverRandomMedia.vue'
import MediaBoard from '../components/MediaBoard.vue'

export default {
  name: 'Home',
  components: {
    MediaBoard,
    CoverRandomMedia,
  }
}
</script>

<style>
  .home {
    background-color: rgb(0, 10, 10);
  }
</style>
