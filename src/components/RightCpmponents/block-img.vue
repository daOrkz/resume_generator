<template>
<div>
  <img class="avatar" :src="text" alt=""> <button @click="$emit('action')">Del</button>
</div>
</template>

<script>
export default {
props: ['text']
}
</script>

<style>

</style>