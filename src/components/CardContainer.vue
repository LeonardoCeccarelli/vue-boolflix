<template>
  <div>
    <ul class="card_container" v-for="(data, i) in this.mainData" :key="i">
      <h2 v-if="data.array.length" class="title_section">{{ data.title }}</h2>
      <SingleCard
        v-for="movie in data.array"
        :key="movie.id"
        :title="movie.title ? movie.title : movie.name"
        :originalTitle="
          movie.original_title ? movie.original_title : movie.original_name
        "
        :language="movie.original_language"
        :vote="movie.vote_average"
        :url="movie.poster_path"
        :overview="movie.overview"
      ></SingleCard>
    </ul>
  </div>
</template>

<script>
import SingleCard from "./SingleCard.vue";
export default {
  name: "CardContainer",
  components: { SingleCard },
  props: {
    mainData: Array,
  },
  data() {
    return {};
  },
  methods: {},
};
</script>

<style>
</style>