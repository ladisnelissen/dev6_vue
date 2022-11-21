<script setup>
import { ref, onMounted, reactive } from 'vue';

let users = reactive({
    data: [],
})

let comments = reactive({
    data: [],
})

onMounted(() => {
   fetch("https://lab5-p379.onrender.com/api/v1/messages/")
   .then(res => res.json())
   .then(data => {
         //loop through data and get users
         for (let i = 0; i < data.length; i++) {
             users.data.push(data[i].user);
         }

         for (let i = data.length-1; i >= 0; i--) {
             comments.data.push(data[i].text);
         }
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