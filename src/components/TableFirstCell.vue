<script setup>
defineProps(["searchValue"]);
defineEmits(["search"]);
</script>

<template>
  <div>
    <input
      :value="searchValue"
      class="search-input"
      placeholder="search for a word"
      @input="(event) => $emit('search', event.target.value)"
    />
  </div>
</template>

<style scoped>
.search-input {
  font-size: 1.2em;
  padding: 5x 10px;
  margin: 10px 20px;
}
</style>
