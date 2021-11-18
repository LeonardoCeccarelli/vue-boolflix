<template>
  <header class="page_header">
    <nav>
      <div class="nav_title_container">
        <h1>Boolflix</h1>
      </div>
      <div class="nav_form_container">
        <div class="form">
          <div class="warning_value" :class="warningValue ? 'active' : ''">
            <i class="fa fa-times" @click="onResetWarning"></i>
            <p>ATTENZIONE: Devi inserire almeno un carattere!</p>
          </div>
          <input
            type="text"
            v-model="valueToSearch"
            placeholder="Film/Serie TV"
            @keyup.enter="onClickGenerate"
          />
          <button type="button" @click="onClickGenerate">Cerca!</button>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
import axios from "axios";
export default {
  name: "Header",
  components: {},
  data() {
    return {
      listMovies: [],
      listSeries: [],
      apiKey: "a34ccfdb321af0e10bee1440af398702",
      apiUrl: "https://api.themoviedb.org/3",
      valueToSearch: "",
      warningValue: false,
    };
  },
  methods: {
    onGenerateList(type, value, typeArray) {
      this[typeArray] = [];
      axios
        .get(this.apiUrl + type, {
          params: {
            api_key: this.apiKey,
            query: value,
            language: "it",
          },
        })
        .then((resp) => {
          this[typeArray] = resp.data.results;
          this.$emit("switchArray", {
            movies: this.listMovies,
            series: this.listSeries,
          });
        });
    },

    onClickGenerate() {
      if (this.valueToSearch.trim(" ") === "") {
        this.warningValue = true;
        return;
      }

      this.warningValue = false;

      this.onGenerateList(
        "/search/tv",
        this.valueToSearch.trim(" "),
        "listSeries"
      );
      this.onGenerateList(
        "/search/movie",
        this.valueToSearch.trim(" "),
        "listMovies"
      );
    },

    onResetWarning() {
      this.warningValue = false;
    },
  },
};
</script>

<style>
</style>