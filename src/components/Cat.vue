<template>
  <v-card>
    <!-- TODO: styling in css, not here! -->
    <v-img :src="image.url" contain></v-img>
    <v-card-actions class="justify-space-between">
      <v-btn @click="vote('like')" color="error" dark>dislike</v-btn>
      <v-btn @click="vote('skip')" color="warning" dark>skip</v-btn>
      <v-btn @click="vote('like')" color="success" dark>like</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Cat',
  data: function() {
    return {
      image: { url: '' },
    };
  },
  created() {
    this.loadNextImage();
  },
  methods: {
    async loadNextImage() {
      try {
        axios.defaults.headers.common['x-api-key'] =
          process.env.VUE_APP_API_KEY;

        let response = await axios.get(
          'https://api.thecatapi.com/v1/images/search',
          { params: { limit: 1, size: 'full' } },
        );

        this.image = response.data[0];
      } catch (err) {
        console.log(err);
      }
    },
    vote(value) {
      this.$emit('vote', value);
      this.loadNextImage();
    },
  },
};
</script>

<style scoped>
#cat {
  height: 80%;
  width: auto;
}
.v-card {
  height: 80%;
  width: auto;
}
</style>
