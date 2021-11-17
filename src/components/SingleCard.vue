<template>
  <li class="card_element">
    <div class="single_card_container">
      <img
        class="path_image"
        :src="
          url ? defaultPathUrl + url : require('../assets/path-default.png')
        "
        alt=""
      />
      <div class="content_single_card">
        <h3>Titolo: {{ title }}</h3>
        <h4>Titolo originale: {{ originalTitle }}</h4>
        <img
          class="flag_image"
          :src="require('../assets/' + getRightFlag(language))"
          alt="flag logo"
        />
        <h4>Voto: {{ vote }}</h4>
      </div>
    </div>
  </li>
</template>

<script>
export default {
  name: "SingleCard",
  component: {},
  props: {
    title: String,
    originalTitle: String,
    language: String,
    vote: Number,
    url: String,
  },
  data() {
    return {
      langFlag: "",
      defaultPathUrl: "https://image.tmdb.org/t/p/w342",
    };
  },
  methods: {
    getRightFlag(lang) {
      switch (lang) {
        case "it":
          this.langFlag = "flag-ita.png";
          break;

        case "en":
          this.langFlag = "flag-eng.png";
          break;

        case "de":
          this.langFlag = "flag-ger.jpg";
          break;

        case "es":
          this.langFlag = "flag-esp.png";
          break;

        case "fr":
          this.langFlag = "flag-fra.jpeg";
          break;

        default:
          this.langFlag = "flag-default.png";
          break;
      }

      return this.langFlag;
    },
  },
};
</script>

<style>
</style>