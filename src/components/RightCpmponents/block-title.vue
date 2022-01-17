<template>
<div>
  <h1>{{text}}</h1> <button @click="$emit('action')">Del</button>
</div>
</template>

<script>
export default {
props: ['text']
}
</script>

<style>

</style>