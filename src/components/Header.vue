<template>
  <header>
    <section id="title">
      <h1>Unsplash Photo Finder</h1>
    </section>
    <section id="search-form">
      <input v-model="search" placeholder="Search"/>
      <button @click="handleSubmit">Search</button>
    </section>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      search: "",
    };
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.$emit('search', this.search);
      this.search = "";
    },
  }
}
</script>

<style scoped>
  @import url("https://fonts.googleapis.com/css?family=Satisfy&display=swap");
  @import url("https://fonts.googleapis.com/css?family=Source+Code+Pro:400,700&display=swap");

  header {
    width: 100%;
    height: 30vh;
    border-radius: 0 0 80% 80% / 10%; 
    background-image: url('../assets/mountains_fog_peaks_135332_1920x1080.jpg');
    background-size: cover;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    padding: 0 2.5%;
  }
  h1 {
    font-family: "Satisfy", cursive;
    font-size: 3.5em;
    color: white;
    text-shadow: 8px -6px 10px #000000c2;
  }
  #search-form {
    height: 50px;
    display: flex;
    justify-content: center;
    height: 75%;
    align-items: center;
  }
  input {
    box-shadow: 9px -7px 20px 0px #000000c2;
    width: 300px;
    text-align: center;
    height: 50px;
    border-radius: 10px 0px 0px 10px;
    border: none;
    font-size: 1.5em;
    font-family: "Source Code Pro", sans-serif;
  }
  button {
    box-shadow: 9px -7px 20px 0px #000000c2;
    width: 100px;
    height: 50px;
    border-radius: 0px 10px 10px 0px;
    border: none;
    border-left: 1px solid #ccc;
    background-color: black;
    color: white;
    font-size: 1.2em;
    border: solid white 1px;
    font-family: "Source Code Pro", sans-serif;
  }
  button:hover {
    cursor: pointer;
  }
</style>