<template>
  <section id="page-nav">
    <span 
      v-for="page in [1,2,3,4,5]" 
      v-bind:key="page"
      @click="$emit('change-page', page)"
      class="page"
    >
      {{page}}
    </span>
  </section>
</template>

<script>
export default {
  name: "ImagePageNav",
}
</script>

<style scoped>
  .page:hover {
    cursor: pointer;
  }
</style>