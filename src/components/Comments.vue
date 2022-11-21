<script setup>
import { ref, onMounted, reactive } from 'vue';
let user = ref("");
let text = ref("");
</script>

<template>
 <div>
    <h3>{{user}}</h3>
    <p>{{text}}</p>
 </div>  
</template>

<style scoped>

</style>