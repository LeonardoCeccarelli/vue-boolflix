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
        <h4>Titolo: {{ title }}</h4>
        <h4>Titolo originale: {{ originalTitle }}</h4>
        <img
          class="flag_image"
          :src="require('../assets/' + getRightFlag(language))"
          alt="flag logo"
        />
        <h4 v-if="vote">
          Voto:
          <span v-for="(star, i) in getRightVote(vote)" :key="i">
            <i :class="star"></i>
          </span>
        </h4>
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
      defaultPathUrl: "https://image.tmdb.org/t/p/w342",
    };
  },
  methods: {
    getRightFlag(lang) {
      let langFlag = "";

      switch (lang) {
        case "it":
          langFlag = "flag-ita.png";
          break;

        case "en":
          langFlag = "flag-eng.png";
          break;

        case "de":
          langFlag = "flag-ger.jpg";
          break;

        case "es":
          langFlag = "flag-esp.png";
          break;

        case "fr":
          langFlag = "flag-fra.png";
          break;

        default:
          langFlag = "flag-default.png";
          break;
      }

      return langFlag;
    },
    getRightVote(number) {
      let int = Math.ceil(number / 2);
      const starFull = "fa fa-star";
      const starEmpty = "fa fa-star-o";
      const listStar = [];
      while (listStar.length < 5) {
        if (int > 0) {
          listStar.push(starFull);
          int--;
        } else {
          listStar.push(starEmpty);
        }
      }
      return listStar;
    },
  },
};
</script>

<style>
</style>