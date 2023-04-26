<template>
<div class="container">
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

<style lang="scss" scoped>

</style>