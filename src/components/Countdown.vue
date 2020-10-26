<template>
  <v-container fluid>
    <v-row>
      <v-progress-linear :value="getValue"></v-progress-linear>
    </v-row>
    <v-row>
      <span v-if="!timeout">
        {{ currentTime }}
      </span>
      <span v-else>Time is up!</span>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'Countdown',
  props: {
    time: {
      type: Number,
      required: true,
    },
  },
  data: function() {
    return {
      currentTime: 0,
      timeout: false,
    };
  },
  computed: {
    getValue() {
      return (100 * this.currentTime) / this.time;
    },
  },
  watch: {
    currentTime: {
      handler(value) {
        if (value < this.time) {
          setTimeout(() => {
            this.currentTime++;
          }, 1000);
        } else {
          this.timeout = true;
          this.$emit('timeout');
        }
      },
      immediate: true, // This ensures the watcher is triggered upon creation
    },
  },
};
</script>
