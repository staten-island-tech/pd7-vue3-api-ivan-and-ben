<template>
    <div>
  <Bar v-if="check" :data="data"/>
    </div>
  </template>
  
  <script>
  import { Bar } from 'vue-chartjs'
  import { onMounted } from 'vue'
  import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
  ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
  
  export default {
    name:"BarChart2",
    components:{
      Bar
    },
    data: () => ({
      check: false,
      data:{
        labels:["Staten Island" , "Kingsbridge - Riverdale" , "Sunset Park"],
        datasets:[{ data: [],
        label:"AQI" ,
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
      },
    methods:{
      change:  onMounted(async () => {
  
      })
    }
    }),
  
    async mounted () {
      try {
        let res2 = await fetch(
      "https://data.cityofnewyork.us/resource/c3uy-2p5r.json"
    );
    let data2 = await res2.json();
    let arr = Object.values(data2)
    console.log(data2)
   let Staten = arr.filter((uid) => uid.unique_id === "130444")
    console.log(Staten[0].data_value)
    let kings = arr.filter((uid) => uid.unique_id === "131555")
    console.log(kings[0].data_value)
    let sun = arr.filter((uid) => uid.unique_id === "131566")
    console.log(sun[0].data_value)
    this.data.datasets[0].data.push(Staten[0].data_value , kings[0].data_value , sun[0].data_value)
    console.log(Staten[0].data_value , kings[0].data_value , sun[0].data_value)
    this.check = true
  
      } catch (e) {
        console.error(e)
      }
  }};
  </script>
  
  <style lang="scss" scoped>
  
  </style>