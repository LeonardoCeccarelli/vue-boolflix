<template>
  <ul class="card_container">
    <SingleCard
      v-for="movie in this.array"
      :key="movie.id"
      :title="movie.title ? movie.title : movie.name"
      :originalTitle="
        movie.original_title ? movie.original_title : movie.original_name
      "
      :language="movie.original_language"
      :vote="movie.vote_average"
      :url="movie.poster_path"
    ></SingleCard>
  </ul>
</template>

<script>
import SingleCard from "./SingleCard.vue";
export default {
  name: "CardContainer",
  components: { SingleCard },
  props: {
    array: Array,
  },
  data() {
    return {};
  },
  methods: {},
};
</script>

<style>
</style>