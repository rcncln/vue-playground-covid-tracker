<template>
  <div>
    <div class="box-container">
      <div class="box-wrapper">
        <div v-once>{{ title }}</div>
        <div>
          New: <strong>{{ numberWithCommas(newConfirmed) }}</strong>
        </div>
        <div>
          Total: <strong>{{ numberWithCommas(totalConfirmed) }}</strong>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DataBox",
  props: ["newConfirmed", "totalConfirmed", "title"],
  setup() {
    return {
      numberWithCommas(x) {
        return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
      },
    };
  },
};
</script>

<style scoped>
.box-container {
  width: 300px;
  height: 200px;
  background-color: cadetblue;
  border-radius: 12px;
  box-shadow: 5px 5px 15px 0px gray;
}

.box-wrapper {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  flex-direction: column;
  padding: 20px;
}

.box-wrapper div {
  padding: 15px;
}
</style>