<template>
  <div id="container">
    <div id="image-card-container">
      <ImageCard 
      v-bind:key='image.id' 
      v-for='image in images'
      v-bind:image='image' 
      />
    </div>
  </div>
</template>

<script>
import ImageCard from './ImageCard';
export default {
  name: 'ImageContainer',
  props: ['images'],
  components: {
    ImageCard,
  },
}
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  #image-card-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    align-items: center;
  }
</style>