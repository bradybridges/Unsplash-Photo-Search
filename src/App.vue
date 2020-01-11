<template>
  <div id="app">
    <h1 v-if="error !== ''">{{error}}</h1>
    <ImagePageNav v-on:change-page="updatePage"/>
    <SearchBar v-bind:defaultSearch="defaultSearch" v-on:search="search"/>
    <ImageContainer v-bind:images='images.results' v-if='images'/>
  </div>
</template>

<script>
import { key } from '../key';
import Unsplash from 'unsplash-js';
import ImageContainer from './components/ImageContainer';
import SearchBar from './components/SearchBar';
import ImagePageNav from './components/ImagePageNav';
const unsplash = new Unsplash({ accessKey: key });

export default {
  name: 'app',
  components: {
    ImageContainer,
    SearchBar,
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
    };
  },
  created() {
    unsplash.search.photos('mountains', this.currentPage, this.imgsPerPage, { orientation: 'portrait' })
    .then((data) => data.json())
    .then((images) => this.images = images)
    .catch((err) => this.error = err);
  },
  methods: {
    search(searchValue, page = 1) {
      this.currentPage = page;
      this.currentSearch = searchValue;
      unsplash.search.photos(searchValue, this.currentPage, this.imgsPerPage, { orientation: 'portrait' })
      .then((data) => data.json())
      .then((images) => this.images = images)
      .catch((err) => this.error = err);
    },
    updatePage(num) {
      if(this.currentPage === num) return;
      this.currentPage = num;
      const search = this.currentSearch;
      this.search(search, num);
    },
    updateImgsPerPage(num) {
      this.imgsPerPage = num;
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
