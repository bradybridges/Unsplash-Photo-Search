<template>
  <section id="page-nav">
    <span>Prev</span>
    <span 
      v-for="page in [1,2,3,4,5]" 
      v-bind:key="page"
      @click="$emit('change-page', page)"
    >
      {{page}}
    </span>
    <span>Next</span>
  </section>
</template>

<script>
export default {
  name: "ImagePageNav",
}
</script>

<style scoped>

</style>