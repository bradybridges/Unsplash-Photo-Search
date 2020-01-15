<template>
  <section id="page-nav">
    <p 
      v-for="page in [1,2,3,4,5]" 
      v-bind:key="page"
      @click="$emit('change-page', page)"
      class="page"
    >
      {{page}}
    </p>
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
    background-color: black;
    color: white;
    border-radius: 4px;
    display: flex;
    justify-content: space-around;
    padding: 10px;
    position: absolute;
    top: 95vh;
    height: 40px;
    z-index: 5;
    border: solid rgba(255, 255, 255, 0.548) 1px;
  }

</style>