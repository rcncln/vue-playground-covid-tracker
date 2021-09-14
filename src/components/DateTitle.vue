<template>
  <div>
    <div class="country">{{ text }}</div>
    <div class="timestamp">{{ timestamp }}</div>
  </div>
</template>

<script>
import dayjs from "dayjs";
import { computed, ref } from "vue";

export default {
  name: "DateTitle",
  props: {
    text: String,
    dateStamp: Number,
  },
  setup(props) {
    const { dateStamp } = ref(props);

    return {
      timestamp: computed(() =>
        dayjs(dateStamp).format("MMMM DD YYYY, hh:mm A")
      ),
    };
  },
};
</script>

<style scoped>
.country {
  font-size: 24px;
  padding: 50px 0 2px 0;
  white-space: nowrap;
  letter-spacing: 1px;
  font-weight: 700;
  text-transform: uppercase;
}

.timestamp {
  font-style: italic;
  opacity: 0.7;
}
</style>