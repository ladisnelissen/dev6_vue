<script setup>
import VideoPlayer from './components/VideoPlayer.vue';
import VideoDetails from './components/VideoDetails.vue';
import Comments from './components/Comments.vue';

</script>

<template>
  <div class="app">
    <VideoPlayer />
    <div.sidebar>
      <VideoDetails />
      <Comments />
    </div.sidebar>
  </div>
  
</template>

<style scoped>
.app {
  display: grid;
  grid-template-columns: 4fr 2fr;
}
</style>
