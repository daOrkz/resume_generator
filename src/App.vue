<template>
  <div class="cont">
    <div class="flex">
      <app-left @create-block="AddBlock"></app-left>
      <app-right :blocks="block"></app-right>
    </div>
    <app-button v-if="!TenComments.length" @click="LoadComments">Commits</app-button>
    <app-comments v-if="TenComments" :comments="TenComments"></app-comments>
  </div>
</template>

<script>
import AppComments from "./components/AppComments.vue"
import AppButton from "./components/AppButton.vue"
import AppLeft from "./components/AppLeft.vue"
import AppRight from "./components/AppRight.vue"

export default {
  data() {
    return {
      block: [],
      TenComments: []
    }
  },
  methods: {
    AddBlock(data) {
      this.block.push(data)
    },
    async LoadComments() {
      const response = await fetch('https://jsonplaceholder.typicode.com/comments')
        
      const comments = await response.json()
      

      for (let i = 0; i < 10; i++) {
        this.TenComments.push(comments[i])
      }
    }
  },
  components: {AppLeft, AppRight, AppButton, AppComments}
}
</script>

<style>

</style>