<template>
<div class="right">
  <component 
    v-for="block in blocks"
    :key="block"
    :is="'block-' + block.title"
    :text="block.text"
  ></component>
</div> 
</template>

<script>
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
  components: {BlockAvatar,BlockSubtitle,BlockText,BlockTitle}
}
</script>

<style>

</style>