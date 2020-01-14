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
    height: 50px;
    display: flex;
    justify-content: center;
    background-color: blue;
    width: 100%;
    height: 250px;
    align-items: center;
  }
  input {
    width: 300px;
    text-align: center;
    height: 50px;
    border-radius: 10px 0px 0px 10px;
    border: none;
  }
  button {
    width: 100px;
    height: 50px;
    border-radius: 0px 10px 10px 0px;
    border: none;
    border-left: 1px solid #ccc;
  }
</style>