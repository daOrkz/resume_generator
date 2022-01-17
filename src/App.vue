<template>
  <div class="cont">
    <div class="flex">
      <app-left @create-block="AddBlock" @load-resume="loadResume"></app-left>
      <app-right :blocks="block" @delete-block="removeBlock"></app-right>
    </div>
    <app-button v-if="!TenComments.length" @click="LoadComments">Commits</app-button>
    <app-comments v-if="TenComments" :comments="TenComments"></app-comments>
  </div>
  <h3>{{block}}</h3>
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
      fullResume: null,
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
    },
    loadResume(data) {

      this.fullResume = Object.keys(data).map(key => {
        return { 
          id: key,
          title: data[key].title,
          text: data[key].text
        }
      })
      this.block = this.fullResume
    },
    removeBlock(data) {
      let idBlock = this.block[data].id
      this.block.splice(data, 1)
      fetch(`https://testo-1fe49-default-rtdb.firebaseio.com/resume/${idBlock}.json`, {
        method: "DELETE"
      })

    }
  },
  components: {AppLeft, AppRight, AppButton, AppComments}
}
</script>

<style>

</style>