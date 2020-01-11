<template>
  <div id="app">
    <ImageContainer v-bind:images='images.results' v-if='images'/>
  </div>
</template>

<script>
import { key } from '../key';
import Unsplash from 'unsplash-js';
import ImageContainer from './components/ImageContainer';
const unsplash = new Unsplash({ accessKey: key });

export default {
  name: 'app',
  components: {
    ImageContainer
  },
  data() {
    return {
      images: null,
      error: '',
    };
  },
  created() {
    unsplash.search.photos('puppies', 1, 10, { orientation: 'portrait' })
    .then((data) => data.json())
    .then((images) => this.images = images)
    .catch((err) => this.error = err);
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
  margin-top: 60px;
}
</style>
