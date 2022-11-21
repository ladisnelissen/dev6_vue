<script setup>
import { ref, onMounted, reactive } from 'vue';
let user = ref("");
let text = ref("");



onMounted(() => {
   fetch("https://lab5-p379.onrender.com/api/v1/messages/")
   .then(res => res.json())
   .then(data => {
      user.value = data.user;
      text.value = data.text;

      console.log(data[0].user);
   })
 
   });

</script>

<template>
 <div>
    <h3>{{user}}</h3>
    <p>{{text}}</p>
 </div>  
</template>

<style scoped>

</style>