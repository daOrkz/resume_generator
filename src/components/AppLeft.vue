<template>
  <div class="left">
    <form action="" @submit.prevent="AddBlock" @keydown.enter="AddBlock">
      <selct v-model:value="title"></selct>
      <inpt v-model:value="text"></inpt>
      <app-button>Create</app-button>
    </form>
  </div>
</template>

<script>
import selct from "./LeftComponents/select.vue"
import inpt from "./LeftComponents/input.vue"
import AppButton from "./AppButton.vue"

export default {
  data() {
    return {
      title: 'title',
      text: ''
    }
  },
  methods: {
    AddBlock() {
      this.$emit('create-block', {
        title: this.title,
        text: this.text
      })
      this.text = ""
    }
  },
  components: {selct, inpt, AppButton}
}
</script>

<style>

</style>