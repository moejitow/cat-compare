<template>
    <v-app-bar
      app
      color="green darken-3"
      dark
    >
    <!-- TODO: credit flaticon author -->
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="@/assets/cat.svg"
          transition="scale-transition"
          width="40"
        />
        <span class="ml-2"><h1>Cat Compare</h1></span> 
      </div>

      <v-spacer></v-spacer>

      <!-- TODO: add color and margin in css not here -->
      <router-link style="color: white" class="mr-5" to="/"><h2>Home</h2></router-link>
      <router-link style="color: white" class="mr-5" to="/about"><h2>About</h2></router-link>
    </v-app-bar>
</template>