<template>
  <div class="wrapper">
  <!-- <header></header> -->
    <div class="wrapper-content">

      <section>
        <div class="container">

          <button class="btn btnPrimary" @click="modalFirst = !modalFirst">Show first modal</button>
          <!-- first modal -->
          <Modal
              title="First modal"
              v-if="modalFirst"
              @close="modalFirst = !modalFirst"
          >
          </Modal>
        </div>
      </section>
      
    </div>
  </div>
</template>

<script>

import Modal from "./components/Modal";
export default {
  components: {
    Modal
  },
  data () {
    return {
      modalFirst: false
    }
  }
}
</script>
