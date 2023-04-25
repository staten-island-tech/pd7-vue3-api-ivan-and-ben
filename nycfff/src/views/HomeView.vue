<template>
  <div>
    <h1>preevyet</h1>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
const test = ref("");
async function getCause() {
  let res = await fetch(
    "https://data.cityofnewyork.us/resource/jb7j-dtam.json"
  );
  let data = await res.json();
  test.value = data;
  console.log(test.value);
}
onMounted(() => {
  getCause();
});
</script>

<style scoped></style>
