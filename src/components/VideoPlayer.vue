<script setup>
import { ref, onMounted, reactive } from 'vue';
import 'animate.css';

let videos = reactive({
    data: [],
})
let videoSrc = ref("")
let counter = ref(0);
let animation = ref("");

onMounted(() => {
    fetch("https://app.fakejson.com/q/1yx40sPr?token=1b0YzS-TYYB4rgrqRl5vpQ")
    .then(res => res.json())
    .then(data => {
        //get first video
        videos.data = data.videos;
        videoSrc.value = data.videos[0].video;
  
    })
});

const nextVideo = () => {
    animation.value="animate__fadeOut";
    counter.value++;
    setTimeout(() => {
        videoSrc.value = videos.data[counter.value].video;
        animation.value="animate__fadeIn";
    }, 500);
    
}

</script>

<template>
  <div class="blur">
    {{counter}}
    <div class="controls">
        <a @click.prevent="nextVideo" href="#">👉</a>

    </div>
    <video 
    :src="videoSrc" 
    :class="animation"
    class="animate__animated"
    controls></video>
  </div>
  
</template>

<style scoped>
    video {
        max-width: 100%;
        max-height: 100vh;
    }

    .blur {
        background-image: url("/blurry.png");
        background-size: cover;
        text-align: center;
    }

    .controls {
        position: absolute;
        top: 50%;
        left: 60%;
        transform: translate(-50%, -50%);
        z-index: 1;
    }
</style>