<template>
  <div id="app">
    <h1 v-if="error !== ''">{{error}}</h1>
    <Header v-bind:defaultSearch="defaultSearch" v-on:search="search" v-on:change-img-count="updateImgsPerPage"/>
    <ImagePageNav v-on:change-page="updatePage"/>
    <ImageContainer v-bind:images='images.results' v-if='images && !noImages'/>
    <h2 v-if="noImages">No images found</h2>
  </div>
</template>

<script>
import { key } from '../key';
import Unsplash from 'unsplash-js';
import ImageContainer from './components/ImageContainer';
import ImagePageNav from './components/ImagePageNav';
import Header from './components/Header';
const unsplash = new Unsplash({ accessKey: key });

export default {
  name: 'app',
  components: {
    ImageContainer,
    Header,
    ImagePageNav,
  },
  data() {
    return {
      images: null,
      error: '',
      defaultSearch: 'Mountains',
      currentSearch: 'Mountains',
      currentPage: 1,
      imgsPerPage: 10,
      noImages: false,
    };
  },
  created() {
    unsplash.search.photos('mountains', this.currentPage, this.imgsPerPage, { orientation: 'portrait' })
    .then((data) => data.json())
    .then((images) => this.images = images)
    .catch((err) => this.error = err);
  },
  methods: {
    search(searchValue, page = 1, numImgs) {
      this.currentPage = page;
      this.currentSearch = searchValue;
      this.imgsPerPage = Number(numImgs);
      unsplash.search.photos(searchValue, this.currentPage, this.imgsPerPage, { orientation: 'portrait' })
      .then((data) => data.json())
      .then((images) => {
        if(!images.results.length) return this.noImages = true
        this.images = images;
        this.noImages = false;
      })
      .catch((err) => this.error = err);
    },
    updatePage(num) {
      if(this.currentPage === num) return;
      this.currentPage = num;
      const search = this.currentSearch;
      const imgsPerPage = this.imgsPerPage;
      this.search(search, num, imgsPerPage);
    },
    updateImgsPerPage(num) {
      this.imgsPerPage = Number(num);
      const search = this.currentSearch;
      const page = this.currentPage;
      const numImgs = this.imgsPerPage;
      this.search(search, page, numImgs);
    }
  },
}
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Courgette&display=swap");
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

body {
  background-image: url("./assets/memphis-mini-dark.png");
  background-repeat: repeat;
  background-attachment: fixed;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
}
</style>
