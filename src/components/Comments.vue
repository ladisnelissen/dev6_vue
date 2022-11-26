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

   const addComment = () => {
    comments.comment.push({
        user: "Ladis",
        text: comment.value})

    fetch(api_url, {
        method: "POST",
        headers: {
        "Content-Type": "application/json",
        },
            body: JSON.stringify({
            user: "Ladis",
            text: comment.value,
        }),
    });
        comment.value = "";
    };


</script>

<template>
 <div>
    <div v-for="comment in comments.data" :key="comment.id">
        <h3>{{comment.user}}</h3>
        <p>{{comment.text}}</p>
    </div>
    <button @click="addComment">Add Comment</button>

</div>

</template>

<style scoped>
      div {
         padding: 0 2rem;
         max-height: 450px;
         overflow-y: scroll;
      }
</style>