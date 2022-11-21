<script setup>

import { ref, onMounted } from 'vue';

let username = ref("");
let description = ref("");

onMounted(() => {
    fetch("https://app.fakejson.com/q/1yx40sPr?token=1b0YzS-TYYB4rgrqRl5vpQ")
        .then(res => res.json())
        .then(data => {
            username.value = data.videos[0].username;
            description.value = data.videos[0].description;
        })
});
</script>

<template>
  <div>
    <h3>{{username}}</h3>
    <p>{{description}}</p>
    <p>{{views}} views</p>

  </div>
  
</template>

<style scoped>
    div {
        padding: 0 2rem;
        max-height: 150px;
    }
</style>