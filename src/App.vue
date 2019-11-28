<template lang="html">
<div class="">
  <h2>Energy Chart</h2>
  <energy-list :formattedEnergy = 'formattedEnergy'></energy-list>
</div>
</template>

<script>

import EnergyList from './components/EnergyList.vue'

export default {
  name: 'app',

  data() {
    return {
      energy: [],
      formattedEnergy:[["Fuel", "Percentage"]],
      selectedData: null
    }
  },


  mounted () {
    fetch('https://api.carbonintensity.org.uk/generation')
    .then(response => response.json())
    .then(one => this.energy = one.data.generationmix)
    // .then(two => this.energy = two.generationmix)
    // .then((data) => {
    //   for (energy in data) {
    //     const formattedData = [];
    //     formattedData.push(energy.fuel);
    //     formattedData.push(energy.perc);
    //     this.formattedEnergy.push(formattedData)
    //   }
    // })
    .then(() => this.energy.forEach(entry => {
      this.formattedEnergy.push(Object.values(entry))
    }))

  },

  components: {
    "energy-list": EnergyList
  }

}
</script>

<style lang="css" scoped>
</style>
