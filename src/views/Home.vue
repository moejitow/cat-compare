<template>
  <div id="home" class="justify-center">
    <Timer v-if="!timerStarted" @game-started="startGame" />
    <v-container v-else>
      <v-row><Countdown :time="time" @timeout="setTimeout"/></v-row>
      <v-row><Cat @vote="addVote"/></v-row>
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
    };
  },
  methods: {
    startGame(value) {
      this.time = value;
      this.timerStarted = true;
      this.timeout = false;
    },
    addVote(value) {
      this.votes[value]++;
    },
    setTimeout() {
      this.timeout = true;
      this.timerStarted = false;
    },
  },
};
</script>

<style scoped>
#home {
  padding: 5em;
}
</style>
