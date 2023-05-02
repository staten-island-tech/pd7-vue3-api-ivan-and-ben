<template>
    <div class="container">    
    <Doughnut
      v-if="loaded"
      :data="data"
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
    data: {
      labels: [],
      datasets: [{
       data: [],
       label: "# of names",
       backgroundColor: [
      'rgba(255, 99, 132, 0.2)',
      'rgba(255,192,171, 0.2)',
      'rgba(255, 159, 64, 0.2)',
      'rgba(255,214,171, 0.2)',
      'rgba(255, 205, 86, 0.2)',
      ],
      borderColor: [
      'rgba(255, 99, 132)',
      'rgba(255,192,171)',
      'rgba(255, 159, 64)',
      'rgba(255,214,171)',
      'rgba(255, 205, 86)',
      ],
      borderWidth: 1
      }]
    },
  }),
  async mounted () {
    try {
      let res2 = await fetch(
    "https://data.cityofnewyork.us/resource/25th-nujf.json"
  );
  let data2 = await res2.json();
  let arr = Object.values(data2);
  let girls = arr.filter((name) => name.gndr === "FEMALE");
  console.log(girls);
  let top5 = girls.sort((a,b) => b.cnt-a.cnt).slice(0,5);
  top5.forEach(name => {
        this.data.labels.push(name.nm)
        this.data.datasets[0].data.push(name.cnt)
      });
    this.loaded = true;
    } catch (e) {
      console.error(e)
    }
  }
 }
</script>