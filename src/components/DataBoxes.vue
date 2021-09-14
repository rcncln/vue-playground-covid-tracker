<template>
  <div class="main">
    <data-box
      :title="cases"
      :newConfirmed="stats.NewConfirmed"
      :totalConfirmed="stats.TotalConfirmed"
    />
    <data-box
      :title="deaths"
      :newConfirmed="stats.NewDeaths"
      :totalConfirmed="stats.TotalDeaths"
    />
  </div>
</template>

<script>
import DataBox from "./DataBox.vue";

export default {
  name: "DataBoxes",
  components: {
    DataBox,
  },
  data() {
    return {
      cases: "Cases",
      deaths: "Deaths",
    };
  },
  props: {
    stats: Object,
  },
};
</script>

<style scoped>
.main {
  width: 40%;
  margin: 40px auto;
  display: flex;
  justify-content: space-between;
}
</style>