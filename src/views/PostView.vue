<template>
  <div class="post">
    <h1>This Is About Post</h1>

    <textarea />
    <ul>
      <li v-for="post in posts" :key="post.id">
        <router-link :to="`/postDetail/${post.id}`">
          {{ post.title }}</router-link
        >
      </li>
    </ul>
  </div>
</template>

<script setup>
//sử đụng v-for để map data
import { ref } from "@vue/reactivity";

const posts = ref([
  {
    id: 1,
    title: "post 1",
  },
  {
    id: 2,
    title: "post 2",
  },
  {
    id: 3,
    title: "post 3",
  },
]);

console.log(posts);
</script>
