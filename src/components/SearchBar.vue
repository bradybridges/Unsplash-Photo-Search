<template>
  <div id="search-form">
    <input @change="handleChange" placeholder="Search"/>
    <button @click="$emit('search', search)">Search</button>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      search: "",
    };
  },
  methods: {
    handleChange(e) {
      this.search = e.target.value;
    },
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