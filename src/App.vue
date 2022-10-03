<script setup>
import TableContainer from "./components/TableContainer.vue";
import { computed, onMounted, ref } from "vue";
import { Index } from "flexsearch";
import questions from "./assets/json/questions.json";
import scores from "./assets/json/scores.json";
import filters from "./assets/json/filters.json";

const searchValue = ref("");
const index = new Index("performance");

onMounted(() => {
  questions.forEach((el) => {
    index.add(el._id, el.labels.en);
  });
});

const search = (newSearchValue) => {
  searchValue.value = newSearchValue;
};

const searchedQuestionsId = computed(() => {
  return searchValue.value && searchValue.value.length > 0
    ? index.search(searchValue.value)
    : questions.map((el) => el._id);
});

const searchedQuestions = computed(() => {
  let sQuestions = [];
  if (searchValue.value && searchValue.value.length > 0) {
    sQuestions = questions.filter((question) => {
      const found = searchedQuestionsId.value.find((sQuestionId) => {
        return sQuestionId == question._id;
      });
      return found;
    });
  } else {
    return questions;
  }
  return sQuestions;
});

const searchedScores = computed(() => {
  const sScores = [];
  scores.forEach((el) => {
    if (
      searchedQuestionsId.value.find((question) => question == el.question_id)
    ) {
      sScores.push(el);
    }
  });
  return sScores;
});
</script>

<template>
  <main>
    <TableContainer
      :headers="filters"
      :data="searchedScores"
      :index-data="searchedQuestions"
      :search-value="searchValue"
      @search="search"
    />
  </main>
</template>

<style scoped>
main {
  width: 100%;
  display: flex;
  align-items: center;
  flex-direction: column;
}
</style>
