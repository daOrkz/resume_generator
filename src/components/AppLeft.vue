<template>
  <div class="left">
    <form action="" @submit.prevent="AddBlock" @keydown.enter="AddBlock">
      <selct v-model:value="title"></selct>
      <inpt v-model:value="text"></inpt>
      <app-button :disabled="disabled">Create</app-button>
      <app-button @click="load">Load</app-button>
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
      text: '',
      dataBaseResume: [],
      dataResume: null,
      baseData: null
    }
  },
  methods: {
    async AddBlock() {
      if (this.text.length > 3) {    
        const response = await fetch('https://testo-1fe49-default-rtdb.firebaseio.com/resume.json', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify({
            title: this.title,
            text: this.text
          })
        })
      
        this.$emit('create-block', {
          title: this.title,
          text: this.text
        })
      }
      this.text = ""
    },
    async load() {
      const response = await fetch('https://testo-1fe49-default-rtdb.firebaseio.com/resume.json')
      this.baseData = await response.json()

      this.$emit('load-resume', this.baseData)
    }
  },
  computed: {
    disabled() {
      if (this.text.length > 3) {
        return false
      } else {
        return true
      }
    }
  },
  components: {selct, inpt, AppButton}
}
</script>

<style>

</style>