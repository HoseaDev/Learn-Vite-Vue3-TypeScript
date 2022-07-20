<template>
  <teleport to="#modal">
    <div class="center" v-if="isOpen">
      <h1>
        <slot>Hello Hosea!.</slot>
      </h1>
      <button @click="handleClose">Close</button>
    </div>

  </teleport>
</template>

<script>
import {defineComponent} from "vue";

export default {

  props: {
    isOpen: Boolean,
  },
  emits: {
    'close-modal': null
  },
  setup(props, context) {
    const handleClose = () => {
      context.emit('close-modal')
    }

    return {handleClose }
  },
  name: "Modal"
}
</script>

<style scoped>
.center {
  position: fixed;
  left: 50%;
  top: 50%;
  border: 5px saddlebrown solid;
  background: #747bff;
  color: white;
}
</style>