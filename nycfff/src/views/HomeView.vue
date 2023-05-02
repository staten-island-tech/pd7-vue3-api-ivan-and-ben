<template>
  <div class="buttons">
    <button id="button" @click="newchart">Switch Parts of NYC</button>
  </div>
  <div v-if="load" >
    <BarChart class="chart" />
  </div>
  <div v-if="load2">
    <BarChart2 class="chart" />
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
.buttons {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}
#button{
  text-decoration: none;
  padding: 2rem 3rem;
  display: block;
  font-size: 2rem;
  border: none;
  border-radius: 10rem;
  transition: all 0.2s;
  text-align: center;
  margin-top: 1rem;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 2rem;
}
#button:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 0.5rem rgba(0, 0, 0, 0.2);
}

</style> 
