<template>
  <Modal
      title="Modal with form"
      @close="$emit('close')"
  >
    <div slot="body">
      <form @submit.prevent="">
        <label>Name:</label>
        <input type="text" required>
        <label>Email:</label>
        <input type="email" required>
        <button class="btn btnPrimary">Submit</button>
      </form>
    </div>
  </Modal>
</template>

<script>
import Modal from "./UI/Modal";

export default {
  name: "ModalValidate",
  components: {Modal}
}
</script>
