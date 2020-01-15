<template>
  <section id="imgs-per-page-option-menu">
    <span>Results Per Page: </span>
    <select @change="handleImgCountChange">  
      <option value="10">10</option>
      <option value="25">25</option>
      <option value="50">50</option>
    </select>
  </section>
</template>

<script>
export default {
  name: "ImagesPerPageOptionsMenu",
  data() {
    return {
      imagesPerPage: 10,
    };
  },
  methods: {
    handleImgCountChange(e) {
      this.imagesPerPage = Number(e.target.value);
      this.$emit('change-img-count', this.imagesPerPage);
    },
  },
}
</script>

<style scoped>
  #imgs-per-page-option-menu {
    background-color: rgba(255, 255, 255, 0.671);
    width: 200px;
    height: 40px;
    position:absolute;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    border-radius: 4px;
    top: 25vh;
    right: 1%;
  }
</style>
