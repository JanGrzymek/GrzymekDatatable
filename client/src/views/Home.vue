<template>
  <v-container>
    <v-alert class="blue-grey darken-2 white--text mx-15">
      Rent selected movies: {{ selected.map((el) => el.title).join(', ') }}</v-alert
    >
    <v-data-table
      class="ma-15"
      v-model="selected"
      :headers="this.headers"
      :items="this.movies"
      :items-per-page="6"
      :footer-props="{ itemsPerPageOptions: [6, 12, 18] }"
      show-select
    >
    </v-data-table>
  </v-container>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Home',
  data() {
    return {
      headers: [
        { text: 'Title', value: 'title' },
        { text: 'Director', value: 'director' },
        { text: 'Genre', value: 'main_genre' },
        { text: 'Year', value: 'year', width: 100 },
        { text: 'Rated', value: 'rated', width: 100 },
        { text: 'Plot', value: 'plot' },
      ],
      movies: [],
      selected: [],
    };
  },
  methods: {
    async getMovies() {
      try {
        const { data } = await axios({
          url: 'http://localhost:3000/movies',
          method: 'GET',
        });
        this.movies = data;
      } catch (error) {
        console.log(error);
      }
    },
  },
  async created() {
    await this.getMovies();
  },
};
</script>
