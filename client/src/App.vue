<template>
  <v-app>
    <v-app-bar class="app-bar" app>
      <img class="image-bar d-none d-md-inline" src="logo.png" />
      <span class="text-h5"> Movies </span>
      <v-spacer></v-spacer>
      <v-btn href="https://www.imdb.com/movies-in-theaters/" depressed
        >LATEST RELEASES
        <v-icon>
          mdi-open-in-new
        </v-icon></v-btn
      >
    </v-app-bar>
    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<style>
.image-bar {
  margin-top: 100px;
  height: 150px;
}

.app-bar {
  color: #e8e8e8;
  height: 200px;
}
</style>

<script>
export default {
  name: 'App',

  data: () => ({
    //
  }),
};
</script>
