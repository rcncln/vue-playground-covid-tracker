<template>
  <header>
    <div class="header-title">Covid Tracker</div>
    <p>
      Api provided by
      <a href="https://covid19api.com">https://covid19api.com</a>
    </p>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped>
header {
  height: 80px;
  text-align: center;
  background-color: darkslategrey;
  padding: 15px 0;
  color: white;
}

.header-title {
  font-size: 24px;
}

a {
  text-decoration: none;
  color: black;
}
</style>