<template>
  <header>
    <section id="title">
      <h1>Unsplash Photo Finder</h1>
    </section>
    <section id="search-form">
      <input @change="handleChange" placeholder="Search"/>
      <button @click="$emit('search', search, null, imgsPerPage)">Search</button>
      <select @change="handleImgCountChange">  
        <option value="10">10</option>
        <option value="25">25</option>
        <option value="50">50</option>
      </select>
    </section>
  </header>
</template>

<script>
export default {
  name: "Header",
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
@import url("https://fonts.googleapis.com/css?family=Satisfy&display=swap");
  header {
     background-color: red;
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

  h1, h4 {
    text-align: left;
    padding-left: 20px;
    color: white;
  }

  h1 {
    font-family: "Satisfy", cursive;
    font-size: 3em;
  }

  h4 {
    font-size: 1.2em;
  }

  #search-form {
    height: 50px;
    display: flex;
    justify-content: center;
    /* width: 100%; */
    height: 75%;
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