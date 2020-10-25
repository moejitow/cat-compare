<template>
  <div class="home">
    <Timer v-if="!timerStarted" @game-started="startGame"/>
    <Countdown v-if="timerStarted" :time="time"/>
  </div>
</template>

<script>
import Timer from '@/components/Timer'
import Countdown from '@/components/Countdown'

export default {
  name: 'Home',
  components: {
    Timer,
    Countdown
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