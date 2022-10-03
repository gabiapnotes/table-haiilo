<script setup>
defineProps(["searchValue"]);
defineEmits(["search"]);
</script>

<template>
  <p>
    <input
      :value="searchValue"
      class="search-input"
      placeholder="search for a word"
      @input="(event) => $emit('search', event.target.value)"
    />
  </p>
</template>

<style scoped>
.search-input {
  font-size: 1.2em;
  padding: 5px;
}
</style>
