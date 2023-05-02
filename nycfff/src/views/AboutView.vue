<template>
  <div class="buttons">
    <button id="button" @click="switchDisplayBoy()">Top 5 Most Common Boys Names</button>
    <button id="button" @click="switchDisplayGirl()">Top 5 Most Common Girls Names</button>
  </div>
  <BoyDoughnutChart class="chart" v-if="this.display ==='boy'"/>
  <GirlDoughnutChart class="chart" v-if="this.display ==='girl'"/>
</template>

<script>
import BoyDoughnutChart from '../components/BoyDoughnutChart.vue';
import GirlDoughnutChart from '../components/GirlDoughnutChart.vue';
export default {
  name: "Home",
  components: {
    BoyDoughnutChart,
    GirlDoughnutChart,
  },
  data() {
    return {
      display: "boy",
    };
  },
  methods: {
    switchDisplayBoy(){
     this.display = "boy"
    },
    switchDisplayGirl(){
     this.display = "girl"
    },
  },
};
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
.chart{
  width: 50%;
  margin: auto;
}
</style>