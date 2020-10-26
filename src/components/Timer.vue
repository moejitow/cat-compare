<template>
  <v-container fluid>
    <v-row class="align-center justify-center">
      Please select a time duration in seconds to play Cat Compare
    </v-row>
    <v-row>
      <v-slider
        v-model="time"
        min="10"
        max="180"
        step="10"
        ticks
        thumb-label
      ></v-slider>
    </v-row>
    <v-row class="align-center justify-center">
      <v-btn
        @click="startGame"
        color="green lighten-4"
        elevation="5"
        large
        >Start Game</v-btn
      >
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'Timer',
  data: function() {
    return {
      time: 10,
    };
  },
  methods: {
    startGame() {
      this.$emit('game-started', this.time);
    },
  },
};
</script>
