<template>
  <p class="text">Title:</p>
  <select class="select" v-model="title" :value="value" @input="input">
    <option value="title">Заголовок</option>
    <option value="avatar">Аватар</option>
    <option value="subtitle">Подзаголовок</option>
    <option value="text">Текст</option>
  </select>
</template>

<script>
export default {
  emits: ['update:value'],
  data() {
    return {
      title: 'title'
    }
  },
  props: {
    value: String
  },
  methods: {
    input(event) {
      this.$emit('update:value', event.target.value)
    }
  }
}
</script>

<style>

</style>