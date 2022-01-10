<template>
  <p class="text">Text</p>
  <textarea rows="10" cols="40" :value="value" @input="input"></textarea>
</template>

<script>
export default {
  emits: ['update:value'],
  data() {
    return {
      text: ''
    }
  },
  props: {
    value: String
  },
  methods: {
    input(event) {
      this.$emit('update:value', event.target.value)
      this.text = ""
    }
  }
}
</script>

<style>

</style>