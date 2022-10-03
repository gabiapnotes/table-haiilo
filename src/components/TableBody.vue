<script setup>
import { ref, watch } from "vue";
import { useScroll } from "@vueuse/core";
import TableData from "./TableData.vue";
import TableDataIndexColumn from "./TableDataIndexColumn.vue";

const props = defineProps(["scrollPositionX", "indexData", "data"]);
const emit = defineEmits(["scrollXHeader"]);
const mainTable = ref(null);
const bodyIndexTable = ref(null);
const { x: mainTableX, y: mainTableY } = useScroll(mainTable);
const { y: bodyIndexTableY } = useScroll(bodyIndexTable);

watch(
  () => props.scrollPositionX,
  (newX) => {
    const { scrollTop } = mainTable.value;
    mainTable.value.scroll(newX, scrollTop);
  }
);

watch(mainTableX, (newX) => {
  emit("scrollXHeader", newX);
});

watch(mainTableY, (newY) => {
  const { scrollLeft } = bodyIndexTable.value;
  bodyIndexTable.value.scroll(scrollLeft, newY);
});

watch(bodyIndexTableY, (newY) => {
  const { scrollLeft } = mainTable.value;
  mainTable.value.scroll(scrollLeft, newY);
});
</script>

<template>
  <div ref="bodyIndexTable" class="body-index-table">
    <TableDataIndexColumn :index-data="indexData" />
  </div>
  <div ref="mainTable" class="main-table">
    <TableData :data="data" />
  </div>
</template>
