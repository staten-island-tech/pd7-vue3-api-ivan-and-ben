<template>
<div id="list">
  <card v-for="name in babyNames"
  :baby="name"/>
</div>
</template>

<script setup>
import {ref, onMounted} from 'vue'
import card from '../components/card.vue';
const babyNames = ref("")
async function getBabies(){
  let res = await fetch('https://data.cityofnewyork.us/resource/25th-nujf.json')
  let data = await res.json()
  babyNames.value = data
}
onMounted(()=>{
 getBabies()
})
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