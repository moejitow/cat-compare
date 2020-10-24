<template>
  <div class="home">
    <Timer v-if="!timerStarted" @game-started="startGame"/>
  </div>
</template>

<script>
import Timer from '@/components/Timer'
export default {
  name: 'Home',
  components: {
    Timer
  },
  data: function() {
    return {
      time: 10,
      timerStarted: false
    }
  },
  methods: {
    startGame (value) {
      this.time = value
      this.timerStarted = true
    }
  }
}
</script>

<style scoped>
.home {
  padding: 5em;
}
</style>