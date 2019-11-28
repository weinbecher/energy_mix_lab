<template lang="html">
<div class="">
  <h2>Energy Chart</h2>
  <energy-list :data = 'data'></energy-list>
</div>
</template>

<script>

import EnergyList from './components/EnergyList.vue'

export default {
  name: 'app',

  data() {
    return {
      data: [],
      selectedData: null
    }
  },


  mounted () {
    fetch('https://api.carbonintensity.org.uk/generation')
    .then(response => response.json())
    .then(one => one.data)
    .then(two => two.generationmix)
    // .then(three => three[0])
    .then(data => this.data = data)

  },

  components: {
    "energy-list": EnergyList
  }

}
</script>

<style lang="css" scoped>
</style>
