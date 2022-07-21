<script lang="ts">
import {ref} from 'vue'
import Modal from "./Modal.vue";
import AsyncShow from "./AsyncShow.vue";
import ShowDog from "./ShowDog.vue";
// import Modal from "./Modal.vue";

export default {
  components: {ShowDog, AsyncShow, Modal},
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
<!--      这里vue3只能识别一层布局，如果是多个布局需要嵌套-->
     <div>
       <show-dog />
       <async-show/>

     </div>
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
