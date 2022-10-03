<script setup>
import { reactive } from "vue";
const props = defineProps(["score"]);

const parseValue = (value) => {
  return parseFloat(value).toFixed(1);
};

const classObject = reactive({
  score_0_lighter: parseFloat(parseValue(props.score / 10)).toFixed(0) == 0,
  score_1_lighter: parseFloat(parseValue(props.score / 10)).toFixed(0) == 1,
  score_2_lighter: parseFloat(parseValue(props.score / 10)).toFixed(0) == 2,
  score_3_lighter: parseFloat(parseValue(props.score / 10)).toFixed(0) == 3,
  score_4_lighter: parseFloat(parseValue(props.score / 10)).toFixed(0) == 4,
  score_5_lighter: parseFloat(parseValue(props.score / 10)).toFixed(0) == 5,
  score_6_lighter: parseFloat(parseValue(props.score / 10)).toFixed(0) == 6,
  score_7_lighter: parseFloat(parseValue(props.score / 10)).toFixed(0) == 7,
  score_8_lighter: parseFloat(parseValue(props.score / 10)).toFixed(0) == 8,
  score_9_lighter: parseFloat(parseValue(props.score / 10)).toFixed(0) == 9,
  score_10_lighter: parseFloat(parseValue(props.score / 10)).toFixed(0) == 10,
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
