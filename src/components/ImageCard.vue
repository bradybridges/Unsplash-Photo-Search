<template>
  <div>
    <img v-bind:src="image.urls.regular" v-bind:alt="image.alt_description" />
    <p>Picture taken by {{image.user.name}}</p>
    <p>@{{image.user.twitter_username}}</p>
  </div>
</template>

<script>
export default {
  name: 'ImageCard',
  props: ['image'],
  data() {
    return {
      url: require('../assets/logo.png'),
    };
  },
}
</script>

<style scoped>
  img {
    width: 50%;
    border-radius: 25px;
  }
</style>