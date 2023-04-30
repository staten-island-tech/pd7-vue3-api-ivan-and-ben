<template>
  <Bar
    id="my-chart-id"
    :options="chartOptions"
    :data="chartData"
  />
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

async function getCause() {
  let res = await fetch(
    "https://data.cityofnewyork.us/resource/jb7j-dtam.json"
  );
  let data = await res.json();
  test.value = data;
  let filter = data.filter((yes)=> yes.sex === "Male");
  let thing = filter
  console.log(thing)
  console.log(test.value); 
}

export default {
  name: 'BarChart',
  components: { Bar },
  data() {
    return {
      chartData: {
        labels: [ 'January', 'February', 'March' ],
        datasets: [ { data: [40, 20, 12] } ]
      },
      chartOptions: {
        responsive: true
      }
    }
  }
}
</script>