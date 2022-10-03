<script setup>
import { reactive } from "vue";
const props = defineProps(["score"]);

const parseValue = (value) => {
  return parseFloat(value).toFixed(1);
};
const classObject = reactive({
  /* classes for background of cells */
  ...Array(10)
    .fill()
    .reduce((acc, _, index) => {
      acc[`score_${index}_lighter`] = Math.trunc(props.score / 10) === index;
      return acc;
    }, {}),
  "padding-cell": true,
});
</script>

<template>
  <p :class="classObject">
    {{ parseValue(score) }}
  </p>
</template>

<style lang="scss" scoped>
@import "./../assets/css/scores.scss";
.padding-cell {
  padding: 0 5px;
}
</style>
