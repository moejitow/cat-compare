<template>
  <div id="home" class="justify-center" v-resize="onResize">
    <Timer v-if="!timerStarted" @game-started="startGame" />
    <v-container v-else fluid>
      <v-row>
        <Countdown :time="time" @timeout="setTimeout" />
      </v-row>
      <v-row class="justify-center">
        <Cat @vote="addVote" :is-mobile="isMobile" />
      </v-row>
    </v-container>
    <Summary v-if="timeout" :votes="votes" />
  </div>
</template>

<script>
import Timer from '@/components/Timer';
import Countdown from '@/components/Countdown';
import Cat from '@/components/Cat';
import Summary from '@/components/Summary';

export default {
  name: 'Home',
  components: {
    Timer,
    Countdown,
    Cat,
    Summary,
  },
  data: function() {
    return {
      time: 10,
      timerStarted: false,
      timeout: false,
      votes: {
        dislikes: 0,
        skipped: 0,
        likes: 0,
      },
      isMobile: false,
    };
  },
  mounted() {
    this.onResize();
  },
  methods: {
    startGame(value) {
      this.reset();
      this.time = value;
      this.timerStarted = true;
    },
    addVote(value) {
      this.votes[value]++;
    },
    setTimeout() {
      this.timeout = true;
      this.timerStarted = false;
    },
    reset() {
      this.time = 10;
      this.timeout = false;
      for (var item in this.votes) {
        this.votes[item] = 0;
      }
    },
    onResize() {
      this.isMobile = window.innerWidth < 600;
    },
  },
};
</script>

<style scoped>
#home {
  margin: 2em;
}
</style>
