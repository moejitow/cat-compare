<template>
  <div id="home" class="justify-center">
    <Timer v-if="!timerStarted" @game-started="startGame" />
    <v-container v-else>
      <v-row><Countdown :time="time"/></v-row>
      <v-row><Cat @vote="addVote"/></v-row>
    </v-container>
  </div>
</template>

<script>
import Timer from '@/components/Timer';
import Countdown from '@/components/Countdown';
import Cat from '@/components/Cat';

export default {
  name: 'Home',
  components: {
    Timer,
    Countdown,
    Cat,
  },
  data: function() {
    return {
      time: 10,
      timerStarted: false,
      votes: {
        dislike: 0,
        skip: 0,
        like: 0,
      },
    };
  },
  methods: {
    startGame(value) {
      this.time = value;
      this.timerStarted = true;
    },
    addVote(value) {
      this.votes[value]++;
    },
  },
};
</script>

<style scoped>
#home {
  padding: 5em;
}
</style>
