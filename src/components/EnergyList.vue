<template lang="html">
  <div class="">
    <span>Energy List</span>

    <GChart type="PieChart" :data="chartData" :options="chartOptions">

      <!-- <ul v-for="(fuel, index) in energy" :fuel= "fuel" :key="index">
        <li>[{{fuel.fuel}},{{fuel.perc}}]</li>

      </ul> -->

    </GChart>


  </div>
</template>

<script>
import { GChart } from "vue-google-charts";
export default {
  name: 'energy-list',

  props:['formattedEnergy'],

  components: {
    GChart
  },


  data () {
    return {
      // Array will be automatically processed with visualization.arrayToDataTable function
      chartData: this.formattedEnergy,
      chartOptions: {
        chart: {
          title: 'Company Performance',
          subtitle: 'Sales, Expenses, and Profit: 2014-2017',
        }
      }
    }
  }
}


</script>

<style lang="css" scoped>
</style>
