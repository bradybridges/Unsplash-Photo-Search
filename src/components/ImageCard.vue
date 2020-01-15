<template>
  <section class="image-container">
    <img v-bind:src="image.urls.regular" v-bind:alt="image.alt_description" />
    <section class="img-details">
      <div class="img-author">
        <p>Taken By {{image.user.name}}</p>
        <p v-if="image.user.twitter_username">@{{image.user.twitter_username}}</p>
      </div>
      <a class="download-btn" v-bind:href="image.urls.full" download target="blank">
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
    padding: 2.5%;
  }
  .download-img {
    width: 30px;
    border-radius: 0px;
  }
  .img-details {
    display: flex;
    justify-content: space-around;
    align-items: center;
    width: 90%;
    margin: 10px auto 0px auto;
    color: white;
  }
  .download-btn:hover {
    cursor: pointer;
  }
  @media only screen and (max-width: 1050px) {
    .image-container {
      width: 33%;
    }
  }
  @media only screen and (max-width: 850px) {
    .image-container {
      width: 50%;
    }
  }
  @media only screen and (max-width: 500px) {
    .image-container {
      width: 90%;
    }
  }
</style>