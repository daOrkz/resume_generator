<template>
<div>
  <p class="text"> {{text}} </p> <button @click="$emit('action')">Del</button>
</div>  
</template>

<script>
export default {
props: ['text']
}
</script>

<style>

</style>