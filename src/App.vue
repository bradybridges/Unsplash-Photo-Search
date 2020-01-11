<template>
  <div id="app">
    <SearchBar v-bind:defaultSearch="defaultSearch" v-on:search="search"/>
    <ImageContainer v-bind:images='images.results' v-if='images'/>
  </div>
</template>

<script>
import { key } from '../key';
import Unsplash from 'unsplash-js';
import ImageContainer from './components/ImageContainer';
import SearchBar from './components/SearchBar';
const unsplash = new Unsplash({ accessKey: key });

export default {
  name: 'app',
  components: {
    ImageContainer,
    SearchBar,
  },
  data() {
    return {
      images: null,
      error: '',
      defaultSearch: 'Mountains',
    };
  },
  created() {
    unsplash.search.photos('mountains', 1, 10, { orientation: 'portrait' })
    .then((data) => data.json())
    .then((images) => this.images = images)
    .catch((err) => this.error = err);
  },
  methods: {
    search(searchValue) {
      unsplash.search.photos(searchValue, 1, 10, { orientation: 'portrait' })
      .then((data) => data.json())
      .then((images) => this.images = images)
      .catch((err) => this.error = err);
    },
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
