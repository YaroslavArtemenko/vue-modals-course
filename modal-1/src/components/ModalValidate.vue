<template>
  <Modal
      title="Modal with form + Validate"
      @close="$emit('close')"
  >
<!--    body-->
    <div slot="body">
      <form @submit.prevent="onSubmit">

<!--        name-->
        <div class="form-item" :class="{ errorInput: $v.name.$error }">
          <label>Name:</label>
          <p class="errorText" v-if="!$v.name.required"> Field is required! </p>
          <p class="errorText" v-if="!$v.name.minLength"> Name must have at least {{ $v.name.$params.minLength.min }} !</p>
          <input
              v-model="name"
              :class="{ error: $v.name.$error }"
              @change="$v.name.$touch()"
          >
        </div>

<!--        email-->
        <div class="form-item" :class="{ errorInput: $v.email.$error }">
          <label>Email:</label>
          <p class="errorText" v-if="!$v.email.required"> Field is required! </p>
          <p class="errorText" v-if="!$v.email.email"> Email is not correct! </p>
          <input
              v-model="email"
              :class="{ error: $v.email.$error }"
              @change="$v.email.$touch()"
          >
        </div>

<!--        button-->
        <button class="btn btnPrimary">Submit</button>
      </form>
    </div>
  </Modal>
</template>

<script>

import {required, minLength, email} from 'vuelidate/lib/validators';

import Modal from "./UI/Modal";

export default {
  name: "ModalValidate",
  components: {Modal},
  data() {
    return {
      name: '',
      email: ''
    }
  },
  validations: {
    name: {
      required,
      minLength: minLength(4)
    },
    email: {
      required,
      email
    }
  },
  methods: {
    onSubmit () {
      this.$v.$touch()
      if (!this.$v.$invalid) {
        const user = {
          name: this.name,
          email: this.email
        }
        console.log(user)

        //DONE!
        this.name = ''
        this.email = ''
        this.$v.$reset()
        this.$emit('close')
      }
    }
  }
}
</script>

<style lang="scss">
.form-item .errorText {
  display: none;
  margin-bottom: 8px;
  font-size: 13.4px;
  color: #de4040;
}
.form-item {
  &.errorInput .errorText {
    display: block;
  }
}
input.error {
  border-color: #de4040;
}
</style>