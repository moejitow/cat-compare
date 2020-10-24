<template>
    <v-container fluid>
        <v-col align="center">
        <span>Please select a time duration in seconds to play Cat Compare</span>
        <v-spacer></v-spacer> 
        <v-slider label="Duration in seconds" v-model="time" min="10" max="180" step="10" ticks thumb-label></v-slider>
        <v-btn @click="startGame" color="green lighten-4" elevation="5" large>Start Game</v-btn>
        </v-col>
    </v-container>
</template>

<script>
export default {
    name: 'Timer',
    data: function() {
        return {
            time: 10
        }
    },
    methods: {
        startGame () {
           this.$emit('game-started', this.time) 
        }
    }
}
</script>

<style scoped>
span {
    font-size: 1.5em;
}
</style>