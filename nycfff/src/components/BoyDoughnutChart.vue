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
       backgroundColor: [],
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
  let boys = arr.filter((name) => name.gndr === "MALE");
  console.log(boys);
  let top5 = boys.sort((a,b) => b.cnt-a.cnt).slice(0,5);
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