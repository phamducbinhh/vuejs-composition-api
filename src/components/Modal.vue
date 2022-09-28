<script>
export default {
  name: "Modal",
  emits: ["hideModal"],
  props: {
    title: {
      type: String,
      required: true,
      default: "No title specified",
    },
  },
};
</script>
<template>
  <teleport to="body">
    <div class="modal">
      <h1>{{ title }}</h1>
      <!-- using slot === childern or outlet in reactjs -->
      <slot />
      <!-- using slot === childern or outlet in reactjs -->
      <button @click="$emit('hideModal')">Hide Modal</button>
    </div>
  </teleport>
</template>

<style scoped>
.modal {
  background: wheat;
  color: #000;
  padding: 10px;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}
</style>
