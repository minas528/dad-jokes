<template>
  <div>
    <nuxt-link to="/jokes">Back to jokes </nuxt-link>
    <h2>{{ joke }}</h2>
    <hr />
    <small>Joke ID: {{ $route.params.id }}</small>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      joke: {}
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };
    try {
      const url = `https://icanhazdadjoke.com/j/${this.$route.params.id}`;
      const res = await axios.get(url, config);
      this.joke = res.data.joke;
      console.log(url, res.data.joke);
    } catch (error) {
      console.log(url, error);
    }
  }
};
</script>

<style></style>
