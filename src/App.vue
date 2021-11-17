<template>
  <div>
    <Header @switchArray="updateList"></Header>
    <main>
      <CardContainer :array="listArray"></CardContainer>
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
      listArray: [],
    };
  },
  methods: {
    updateList(object) {
      this.listArray = [];
      this.listArray.push(...object.movies);
      this.listArray.push(...object.series);
    },
  },
};
</script>

<style lang="scss">
@import "./styles/app.scss";
</style>
