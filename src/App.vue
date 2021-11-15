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
<!--              <p>Text Text Text</p>-->
              <button class="btn btnPrimary">Submit</button>
            </div>
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
      modalFirst: false,
      modalSecond: {
        show: false,
        name: '',
        email: ''
      }
    }
  }
}
</script>
