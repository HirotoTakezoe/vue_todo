<template>
  <div class="hoge">
    <h1>{{ msg }}</h1>
    <p>gitpod</p>
  </div>
</template>

<script>
export default {
  name: 'Hoge',
  data () {
    return {
      msg: 'Test children component!'
    }
  }
}
</script>

<style scoped>
h1 {
  /* font-size: 10%; */
  color: brown;
}
</style>
