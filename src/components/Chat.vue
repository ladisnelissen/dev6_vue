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

         for (let i = 0; i < data.length; i++) {
             comments.data.push(data[i].text);
         }
      })
   }) 

   //send message
    const addComment = () => {
        // get message from input
        let message = document.getElementById("message").value;
        let data = {
            user: "Ladis",
            text: message
        }
        fetch("https://lab5-p379.onrender.com/api/v1/messages/", {
            method: "POST",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify(data)
        })
        .then(res => res.json())
        .then(data => {
            console.log(data);
        })
    }


</script>

<template>
    <div>
    <input id="message" type="text" v-model="message" @keyup.enter="sendMessage">
    <button @click="addComment">Add Comment</button>
    </div>
  
  
</template>

<style scoped>
    div {
        padding: 0 1rem;
        margin-top: 10px;
    }
</style>
