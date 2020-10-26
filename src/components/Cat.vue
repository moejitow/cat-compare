<template>
  <v-card>
    <v-img
      :height="size.height"
      :width="size.width"
      :src="image.url"
      contain
    ></v-img>
    <v-card-actions class="justify-space-between">
      <v-btn @click="vote('dislikes')" color="error" dark large>
        dislike
      </v-btn>
      <v-btn @click="vote('skipped')" color="warning" dark large>
        skip
      </v-btn>
      <v-btn @click="vote('likes')" color="success" dark large
        >like</v-btn
      >
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
  computed: {
    size() {
      if (this.isMobile) {
        return { height: '350px', width: '400px' };
      } else {
        return { height: '750px', width: '800px' };
      }
    },
  },
  props: {
    isMobile: Boolean,
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
>>> .v-btn {
  margin: 10px;
}
</style>
