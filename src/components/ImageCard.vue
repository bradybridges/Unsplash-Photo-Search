<template>
  <section class="image-container">
    <img v-bind:src="image.urls.regular" v-bind:alt="image.alt_description" />
    <section class="img-details">
      <div class="img-author">
        <p>Picture taken by {{image.user.name}}</p>
        <p v-if="image.user.twitter_username">@{{image.user.twitter_username}}</p>
      </div>
      <a class="download-btn" v-bind:href="image.urls.full" download>
        <img class="download-img" src="../assets/download.svg" alt="download image" />
      </a>
    </section>
  </section>
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
  }
  .download-img {
    width: 30px;
    border-radius: 0px;
  }
  .img-details {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 90%;
    margin: 10px auto 0px auto;
    color: white;
  }
  .download-btn:hover {
    cursor: pointer;
  }
</style>