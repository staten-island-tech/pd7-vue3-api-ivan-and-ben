<template>
  <h1 class="title"> Air Qulaity In NYC</h1>
  <button class="button" @click="newchart">Other Parts of NYC</button>
  <div v-if="load" >
    <BarChart />
  </div>
  <div v-if="load2">
    <BarChart2 />
  </div>

</template>

<script setup>
import BarChart from "../components/BarChart.vue";
import BarChart2 from "../components/BarChart2.vue";
</script>

<script>

export default {
  data: () =>({
    load: true,
    load2: false
  }),
  methods: {
    newchart: function(){
      if (this.load === true){
        this.load = false
        this.load2 = true
      }
      else {
        this.load = true
        this.load2 = false
      }
    }
  }
}


</script>

<style scoped>
.button {
  text-align: center;
  font-size: large;
}

.title{
  font-size: x-large;
  text-align: center;
}
</style> 
