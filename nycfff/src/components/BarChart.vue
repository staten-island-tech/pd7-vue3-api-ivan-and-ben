<template>
  <div>
<Bar v-if="loaded" :data="data"/>
  </div>
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name:"BarChart",
  components:{
    Bar
  },
  data: () => ({
    loaded: false,
    data:{
      labels:["Coney Island" , "Brooklyn" , "Bronx"],
      datasets:[{ data: [],
      label:"Nice" ,
      backgroundColor: [
      'rgba(255, 99, 132, 0.2)',
      'rgba(255, 159, 64, 0.2)',
      'rgba(255, 205, 86, 0.2)',
      ],
      borderColor: [
      'rgb(255, 99, 132)',
      'rgb(255, 159, 64)',
      'rgb(255, 205, 86)',
      ],
      borderWidth: 1
      }]
    }}
  ),


  async mounted () {
    try {
      let res2 = await fetch(
    "https://data.cityofnewyork.us/resource/c3uy-2p5r.json"
  );
  let data2 = await res2.json();
  let arr = Object.values(data2)
  console.log(data2)
 let coney = arr.filter((uid) => uid.unique_id === "216498")
  console.log(coney[0].data_value)
  let bronx = arr.filter((uid) => uid.unique_id === "216499")
  console.log(bronx[0].data_value)
  let brook = arr.filter((uid) => uid.unique_id === "219971")
  console.log(brook[0].data_value)
  this.data.datasets[0].data.push(coney[0].data_value , brook[0].data_value , bronx[0].data_value)
  this.loaded = true

    } catch (e) {
      console.error(e)
    }
}};
</script>

<style lang="scss" scoped>

</style>