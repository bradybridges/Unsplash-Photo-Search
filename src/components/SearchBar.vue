<template>
  <div id="search-form">
    <input @change="handleChange" placeholder="Search"/>
    <button @click="$emit('search', search, null, imgsPerPage)">Search</button>
    <select @change="handleImgCountChange">  
      <option value="10">10</option>
      <option value="25">25</option>
      <option value="50">50</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      search: "",
      imgsPerPage: 10,
    };
  },
  methods: {
    handleChange(e) {
      this.search = e.target.value;
    },
    handleImgCountChange(e) {
      this.imgsPerPage = Number(e.target.value);
      this.$emit('change-img-count', this.imgsPerPage);
    }
  }
}
</script>

<style scoped>
  #search-form {
    width: 50%;
    height: 50px;
    display: flex;
    justify-content: center;
    margin-top: 50px;
  }
  input {
    width: 300px;
    text-align: center;
  }
  button {
    width: 100px;
  }
</style>