<template>
  <div>
  <h3>{{text}}</h3> <button @click="$emit('action')">Del</button>
  </div>
</template>

<script>
export default {
props: ['text'],
}

</script>

<style>

</style>