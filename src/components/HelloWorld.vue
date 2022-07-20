<script lang="ts">
import {ref} from 'vue'
import Modal from "./Modal.vue";
import AsyncShow from "./AsyncShow.vue";
// import Modal from "./Modal.vue";

export default {
  components: {AsyncShow, Modal},
  props: {
    msg: ''
  },
  setup() {
    const count = ref(0)
    const modalIsOpen = ref(false)
    const openModal = () => {
      modalIsOpen.value = true
    }
    const onModalClose = () => {
      modalIsOpen.value = false
    }
    return {count, modalIsOpen, openModal, onModalClose}
  }
}
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <button type="button" @click="openModal">Open</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>
  <Suspense>
    <template #default>
      <async-show/>
    </template>
    <template #fallback>
      <h1>loading..</h1>
    </template>
  </Suspense>
  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
    >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>

  <Modal :is-open="modalIsOpen" @close-modal="onModalClose">我是Hosea...</Modal>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
