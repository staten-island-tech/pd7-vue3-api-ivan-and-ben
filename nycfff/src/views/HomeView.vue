<template>
  <h1>Hello</h1>
  <div class="container">
    <NYCdataprop v-for="cause in test" :cause="cause" />
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import NYCdataprop from "../components/NYCdataprop.vue";
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
