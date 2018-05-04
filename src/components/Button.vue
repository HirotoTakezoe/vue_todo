<template>
  <div class="button">
    <button @click=addMsg(message)>Button</button>
    <span>{{ msg }}</span>
  </div>
</template>

<script>
export default {
  props: [
    'message'
  ],
  data () {
    return {
      msg: ''
    }
  },
  methods: {
    addMsg (msg) {
      this.msg = msg;
    }
  }
}
</script>


<style lang="sass" scoped>

</style>
