<template>
  <div>
    <select v-model="selected" v-on:change="onChange">
      <option value="0">select country</option>
      <option
        :value="country.ID"
        v-for="country in countries"
        :key="country.ID"
      >
        {{ country.Country }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "CountryPicker",
  props: ["countries"],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    onChange() {
      const country = this.countries.find((item) => item.ID === this.selected);
      this.$emit("get-country", country);
    },
  },
};
</script>

<style scoped>
select {
  outline: none;
  height: 28px;
  padding-left: 5px;
  border-radius: 12px;
  border-color: #88b8ee;
}

select:focus {
  display: inline-block;
  box-shadow: 0 0 0 2px #88b8ff;
  border-radius: 12px;
}

option {
  border-radius: 12px;
}
</style>