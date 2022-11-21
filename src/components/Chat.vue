<script setup>
import { ref, onMounted, reactive } from 'vue';




</script>

<template>
    <div>
        <input type="text" v-model="message" @keyup.enter="sendMessage">
    <button @click="addComment">Add Comment</button>
    </div>
  
  
</template>

<style scoped>
    div {
        padding: 0 1rem;
        margin-top: 10px;
    }
</style>
