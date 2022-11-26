<script setup>
import { ref, onMounted, reactive } from 'vue';

let comments = reactive({
    data: [],
})

let api = 'https://lab5-p379.onrender.com/api/v1/messages/';

onMounted(() => {
   fetch(api)
   .then(res => res.json())
   .then(data => {
        comments.data = data;
      })
   }) 


</script>

<template>
 <div>
      <Comment v-for="(user, index) in users.data.slice().reverse()" :key="index" :user="user">
         <h3>{{user}}</h3>
         <p>{{comments.data[index]}}</p>
      </Comment>

</div>

</template>

<style scoped>
      div {
         padding: 0 2rem;
         max-height: 450px;
         overflow-y: scroll;
      }
</style>