<template>
  <div class="card">
    <h2>{{ cause.leading_cause }}</h2>
    <h3>{{ cause.deaths }}</h3>
  </div>
</template>

<script setup>
const props = defineProps({
  cause: Object,
});
</script>

<style scoped></style>
