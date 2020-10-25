<template>
  <v-container>
    <v-row class="justify-center"><h1>Summary</h1></v-row>
    <v-row class="justify-space-between">
      <v-alert type="success">
        Likes
      </v-alert>
      {{ votes.likes }}
    </v-row>
    <v-row class="justify-space-between">
      <v-alert color="warning" dark icon="mdi-minus-circle">
        Skipped
      </v-alert>
      {{ votes.skipped }}
    </v-row>
    <v-row class="justify-space-between">
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
};
</script>
