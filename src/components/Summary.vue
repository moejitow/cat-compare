<template>
  <v-container fluid>
    <v-row class="my-2 justify-center"><h1>Summary</h1></v-row>
    <v-row class="justify-space-between align-center">
      <v-alert color="grey darken-1" dark icon="mdi-sigma">
        Total
      </v-alert>
      {{ allVotes }}
    </v-row>
    <v-divider></v-divider>
    <v-row class="justify-space-between align-center">
      <v-alert type="success">
        Likes
      </v-alert>
      {{ votes.likes }}
    </v-row>
    <v-divider></v-divider>
    <v-row class="justify-space-between align-center">
      <v-alert color="warning" dark icon="mdi-minus-circle">
        Skipped
      </v-alert>
      {{ votes.skipped }}
    </v-row>
    <v-divider></v-divider>
    <v-row class="justify-space-between align-center">
      <v-alert color="error" dark icon="mdi-cancel">
        Dislikes
      </v-alert>
      {{ votes.dislikes }}
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'Summary',
  props: {
    votes: {
      type: Object,
      required: true,
    },
  },
  computed: {
    allVotes() {
      return (
        this.votes.likes + this.votes.dislikes + this.votes.skipped
      );
    },
  },
};
</script>

<style scoped>
>>> .v-alert {
  margin: 0px;
}
>>> .v-divider {
  margin: 20px 0 20px 0;
}
</style>
