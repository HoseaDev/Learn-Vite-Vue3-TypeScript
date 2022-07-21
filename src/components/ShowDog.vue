<template>
  <h1>Dog....</h1>
  <img :src="result">
</template>

<script>
import axios from 'axios'

export default {
  name: "ShowDog",
  async setup() {
    const netData = await axios.get("https://dog.ceo/api/breeds/image/random")
    return {
      result: netData.data.message
    }
  }
}

</script>

<style scoped>

</style>