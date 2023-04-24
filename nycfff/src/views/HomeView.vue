<template>
  <div>
    <h1>heelo world</h1>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
const test = ref("");
async function getCause() {
  let res = await fetch(
    "https://data.cityofnewyork.us/resource/jb7j-dtam.json"
  );
  test.value = res;
}
onMounted(() => {
  getCause();
});
</script>

<style scoped></style>
