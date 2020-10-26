<template>
  <v-app-bar app color="green darken-3" dark>
    <div class="d-flex align-center">
      <v-img
        alt="Vuetify Logo"
        class="shrink mr-2"
        contain
        src="@/assets/cat.svg"
        transition="scale-transition"
        width="40"
      />
      <span class="ml-2"><h2>Cat Compare</h2></span>
    </div>

    <v-spacer></v-spacer>

    <router-link class="route-link" to="/"><h2>Home</h2></router-link>
    <router-link class="route-link" to="/about"
      ><h2>About</h2></router-link
    >
  </v-app-bar>
</template>

<style scoped>
>>> .h2 {
  color: white;
  font-size: 10px;
}
>>> .router-link-exact-active {
  color: #ffff00 !important;
}
>>> .route-link {
  color: white;
  margin-right: 5px;
}
</style>
