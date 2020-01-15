<template>
  <div class="image-container">
    <img v-bind:src="image.urls.regular" v-bind:alt="image.alt_description" />
    <p>Picture taken by {{image.user.name}}</p>
    <p v-if="image.user.twitter_username">@{{image.user.twitter_username}}</p>
    <p>{{image.description}}</p>
  </div>
</template>

<script>
export default {
  name: 'ImageCard',
  props: ['image'],
}
</script>

<style scoped>
  img {
    width: 100%;
    border-radius: 25px;
  }

  .image-container {
    width: 25%;
    padding: 50px;
    /* transition: transform .2s; */
  }
  /* .image-container:hover {
    transform: scale(1.1);
    cursor: pointer;
  } */
</style>