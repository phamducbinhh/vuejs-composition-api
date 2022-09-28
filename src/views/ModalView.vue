<script>
import { ref } from "@vue/reactivity";
import Modal from "../components/Modal.vue";
export default {
  name: "ModalView",
  setup() {
    const showModal = ref(false);
    const handleShowModal = () => {
      showModal.value = true;
    };
    const handleHideModal = () => {
      showModal.value = false;
    };
    return {
      showModal,
      handleShowModal,
      handleHideModal,
    };
  },
  components: { Modal },
};
//vuejs 2
// export default {
//   data() {
//     return {
//       showModal: false,
//     };
//   },
//   methods: {
//     handleShowModal() {
//       this.showModal = true;
//     },
//     handleHideModal() {
//       this.showModal = false;
//     },
//   },
// };
//
</script>

<template>
  <div class="modals">
    <h1>Modals</h1>
    <button @click="handleShowModal">Show Modal</button>
    <Modal
      v-if="showModal"
      title="Document Object Modal"
      @hideModal="handleHideModal"
    >
      <!-- using slot === childern or outlet in reactjs -->
      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nihil, quod
        beatae temporibus nostrum dignissimos illo maxime vel ipsum, delectus
        nemo voluptate, cupiditate dolorum aut et. Modi odit autem cumque sit.
      </p>
    </Modal>
  </div>
</template>

<style scoped></style>
