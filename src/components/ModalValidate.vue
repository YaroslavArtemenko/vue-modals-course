<template>
  <Modal
      title="Modal with form"
      @close="$emit('close')"
  >
    <div slot="body">
      <form @submit.prevent="">
        <label>Name:</label>
        <input type="text">
        <label>Email:</label>
        <input type="email">
        <button class="btn btnPrimary">Submit</button>
      </form>
    </div>
  </Modal>
</template>

<script>

import { required, minLength, email } from 'vuelidate/lib/validators'

import Modal from "./UI/Modal";

export default {
  name: "ModalValidate",
  components: {Modal}
}
</script>
