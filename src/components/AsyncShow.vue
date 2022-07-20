<template>
<!--  这里是promise返回的值，这里直接可以用这个result-->
  <h1>{{ result }}</h1>
</template>

<script>
export default {
  name: "AsyncShow",
  setup() {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        return resolve({
          result: 'babala'
        })
      }, 3000)
    })
  }
}
</script>

<style scoped>

</style>