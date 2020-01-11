<template>
  <div>
    <input @change="handleChange" v-bind:placeholder="defaultSearch"/>
    <button @click="$emit('search', search)">Search</button>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  props: ['defaultSearch'],
  data() {
    return {
      search: "",
    };
  },
  methods: {
    handleChange(e) {
      this.search = e.target.value;
    },
  }
}
</script>

<style scoped>

</style>