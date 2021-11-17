<template>
  <div>
    <header class="page_header">
      <nav>
        <div class="nav_title_container">
          <h1>Boolflix</h1>
        </div>
        <div class="nav_form_container">
          <form>
            <input type="text" v-model="valueToSearch" />
            <button type="button" @click="onGenerateList">Cerca!</button>
          </form>
        </div>
      </nav>
    </header>

    <main>
      <ul class="card_container">
        <li v-for="movie in listMovies" :key="movie.id">
          <h3>Titolo: {{ movie.title }}</h3>
          <h4>Titolo originale: {{ movie.original_title }}</h4>
          <h4>Lingua: {{ movie.original_language }}</h4>
          <h4>Voto: {{ movie.vote_average }}</h4>
        </li>
      </ul>
    </main>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  components: {},
  data() {
    return {
      listMovies: [],
      apiKey: "66da9c9715a8aa6ea7123977e1274068",
      apiUrl: "https://api.themoviedb.org/3",
      valueToSearch: "",
    };
  },
  methods: {
    onGenerateList() {
      console.log("chiamata");
      this.listMovies = [];
      axios
        .get(this.apiUrl + "/search/movie", {
          params: {
            api_key: this.apiKey,
            query: this.valueToSearch,
            language: "it",
          },
        })
        .then((resp) => {
          this.listMovies = resp.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
@import "./styles/app.scss";
</style>
