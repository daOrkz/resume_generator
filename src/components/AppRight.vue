<template>
<div class="right">
  <component 
    v-for="(block, ind) in blocks"
    :key="block"
    :is="'block-' + block.title"
    :text="block.text"
    @action="del(ind)"
  >
  </component>
</div> 
</template>

<script>
import AppButton from "./AppButton.vue"
import BlockAvatar from "./RightCpmponents/block-img.vue"
import BlockSubtitle from "./RightCpmponents/block-subtitle.vue"
import BlockText from "./RightCpmponents/block-text.vue"
import BlockTitle from "./RightCpmponents/block-title.vue"

export default {
  props: {
    blocks: {
      type: Object
    }
  },
  methods: {
    del(data) {
      this.$emit('delete-block', data)
    }
  },
  components: {BlockAvatar,BlockSubtitle,BlockText,BlockTitle,AppButton}
}
</script>

<style>

</style>