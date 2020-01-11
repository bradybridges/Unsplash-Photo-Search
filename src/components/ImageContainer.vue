<template>
  <div>
    <div v-bind:key='image.id' v-for='image in images'>
      <ImageCard v-bind:image='image' />
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

</style>