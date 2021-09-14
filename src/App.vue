<template>
  <div>
    <Header />
    <div v-if="loading">fetching data</div>
    <div v-else>
      <date-title :text="title" :dateStamp="dateStamp" />
      <data-boxes :stats="status" />
      <country-picker :countries="countries" @get-country="getCountryData" />
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import DateTitle from "./components/DateTitle.vue";
import CountryPicker from "./components/CountryPicker.vue";
import DataBoxes from "./components/DataBoxes.vue";
import { ref } from "vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    Header,
    DateTitle,
    CountryPicker,
    DataBoxes,
  },
  data() {
    return {
      dateStamp: Date.now(),
      cases: "Cases",
      deaths: "Deaths",
    };
  },
  setup() {
    const loading = ref(true);
    const status = ref({});
    const countries = ref([]);
    const title = ref("Global");

    const fetchCovidData = async () => {
      const { data } = await axios.get("https://api.covid19api.com/summary");
      return data;
    };

    const getCountryData = (country) => {
      status.value = country;
      title.value = country.Country;
    };

    const baseSetup = async () => {
      const data = await fetchCovidData();
      status.value = data.Global;
      countries.value = data.Countries;
      loading.value = false;
    };

    baseSetup();

    return {
      loading,
      title,
      status,
      countries,
      getCountryData,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  padding: 0;
}

body {
  margin: 0;
}
</style>
