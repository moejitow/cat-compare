<template>
  <v-progress-linear
    class="my-4"
    :value="getValue"
  ></v-progress-linear>
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
