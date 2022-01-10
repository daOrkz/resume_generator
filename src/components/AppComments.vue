<template>
  <div class="comments" 
    v-for="comment in comments"
    :key="comment.id"
    >
    <h3> {{comment.email}} </h3>
    <p class="text"> {{comment.body}} </p>
  </div>
</template>

<script>
export default {
  props: {
    comments: {
      type: Array
    }
  }
}
</script>

<style>

</style>