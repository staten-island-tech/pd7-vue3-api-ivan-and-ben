<template>
    <div class="container">    
    <Doughnut
      id="my-chart-id"
      v-if="loaded"
      :options="chartOptions"
      :data="chartData"
    />
    </div>
</template>
  
<script>
  import { Doughnut } from 'vue-chartjs'
  import { Chart as ChartJS, Title, Tooltip, Legend, DoughnutController, ArcElement} from 'chart.js'
  ChartJS.register(Title, Tooltip, Legend, DoughnutController, ArcElement)
  export default {
  name: 'DoughnutChart',
  components: { Doughnut },
  data: () => ({
    loaded: false,
    chartData: null,
  }),
  async mounted () {
    this.loaded = false
    
    try {
      const { babyNames } = await fetch('https://data.cityofnewyork.us/resource/25th-nujf.json')
      this.chartData = {
        labels: [],
        datasets: [ { 
            data: [] 
        } ]
      }
      babyNames.forEach(name => {
        this.chartData.labels.push(name.nm)
        this.chartData.datasets.data.push(name.cnt)
      });
      this.loaded = true
    } catch (e) {
      console.log("error")
    }
  }
 }
</script>