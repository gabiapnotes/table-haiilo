<script setup>
import TableFirstCell from "./TableFirstCell.vue";
import TableHeaderColumns from "./TableHeaderColumns.vue";
import { ref, watch } from "vue";
import { useScroll } from "@vueuse/core";

const props = defineProps(["scrollPositionX", "headers", "searchValue"]);
const emit = defineEmits(["scrollXBody", "search"]);
const element = ref(null);
const { x } = useScroll(element);

watch(x, async (newX) => {
  emit("scrollXBody", newX);
});

watch(
  () => props.scrollPositionX,
  (newX) => {
    element.value.scroll(newX, 0);
  }
);
</script>

<template>
  <div class="table-main-cell">
    <TableFirstCell
      @search="(arg) => $emit('search', arg)"
      :search-value="searchValue"
    />
  </div>
  <div ref="element" class="table-headers-row">
    <TableHeaderColumns :headers="headers" />
  </div>
</template>
