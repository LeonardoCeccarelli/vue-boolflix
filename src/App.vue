<template>
  <div>
    <Header @switchArray="updateList"></Header>
    <main>
      <CardContainer :mainData="listData"></CardContainer>
    </main>
  </div>
</template>

<script>
import CardContainer from "./components/CardContainer.vue";
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: { Header, CardContainer },
  data() {
    return {
      listData: [],
    };
  },
  methods: {
    updateList(object) {
      this.listData = [];
      this.listData.push({
        title: "Film",
        array: object.movies,
      });
      this.listData.push({
        title: "Serie Tv",
        array: object.series,
      });
    },
  },
};
</script>

<style lang="scss">
@import "./styles/app.scss";
</style>
