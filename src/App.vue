<template>
  <div class="wrapper">
    <!-- <header></header> -->
    <div class="wrapper-content">

      <section>
        <div class="container">

          <!-- first modal -->
          <button class="btn btnPrimary" @click="modalFirst = !modalFirst">Show first modal</button>
          <Modal
              title="First modal"
              v-show="modalFirst"
              @close="modalFirst = false"
          >
            <div slot="body">
              <p>Text Text Text</p>
              <button class="btn btnPrimary" @click="modalFirst = !modalFirst">Well Done</button>
            </div>
          </Modal>

          <!-- second modal -->
          <button class="btn btnPrimary" @click="modalSecond.show = !modalSecond.show">Show modal with form</button>
          <Modal
              title="Modal with form"
              v-show="modalSecond.show"
              @close="modalSecond.show = false"
          >
            <div slot="body">
              <form @submit.prevent="submitSecondForm">
                <label>Name:</label>
                <input type="text" required v-model="modalSecond.name">
                <label>Email:</label>
                <input type="email" required v-model="modalSecond.email">
                <button class="btn btnPrimary">Submit</button>
              </form>
            </div>
          </Modal>

<!--          modal with validate-->
          <button class="btn btnPrimary" @click="modalValidate = !modalValidate">Show modal with form + Validate</button>
          <ModalValidate
              v-if="modalValidate"
          ></ModalValidate>
        </div>
      </section>

    </div>
  </div>
</template>

<script>

import Modal from "./components/UI/Modal";
import ModalValidate from "./components/ModalValidate";

export default {
  components: {
    Modal,
    ModalValidate
  },
  data() {
    return {
      modalFirst: false,
      modalSecond: {
        show: false,
        name: '',
        email: ''
      },
      modalValidate: false,
    }
  },
  methods: {
    submitSecondForm () {
      console.log({
        name: this.modalSecond.name,
        email: this.modalSecond.email
      })
      this.modalSecond.name = ''
      this.modalSecond.email = ''
      this.modalSecond.show = false
    }
  }
}
</script>
