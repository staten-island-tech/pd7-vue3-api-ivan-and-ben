<template>
  <BoyDoughnutChart/>
</template>

<script setup>
import {ref, onMounted} from 'vue'
import BoyDoughnutChart from '../components/BoyDoughnutChart.vue';
</script>

<style>


#list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}
.item {
  margin-top: 2rem;
  margin-left: 2rem;
  margin-right: 2rem;
  padding: 2rem;
  background-color: var(--light-blue);
  border: 0.5rem solid var(--purple);
  border-radius: 3rem;
  font-size: var(--h3);
}
</style>