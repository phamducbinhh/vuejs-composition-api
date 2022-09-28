<template>
  <div class="post-detail">
    <h1>This is a post-detail page</h1>
    <p>Display the content of post with ID of {{ $route.params.id }} here !!</p>
    <div>
      <button @click="handleShowId">Show Id</button>
    </div>
    <router-link to="/post">Back</router-link>
  </div>
</template>

<script setup>
import { useRoute } from "vue-router";

const route = useRoute();
const handleShowId = () => {
  alert(route.params.id);
};
</script>
