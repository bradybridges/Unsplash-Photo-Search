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
  .page {
    text-decoration: underline;
  }
  .page:hover {
    font-size: 1.2em;
    cursor: pointer;
    text-decoration: none;
  }
  #page-nav {
    width: 150px;
    background-color: gray;
    display: flex;
    justify-content: space-around;
    padding: 10px;
  }

</style>