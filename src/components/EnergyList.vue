<template lang="html">
  <div class="">
    <span>Energy List</span>

    <ul>
      <list-component v-for="(fuel, index) in data" :fuel= "fuel" :key="index"></list-component>
    </ul>
  </div>
</template>

<script>

import ListComponent from './ListComponent.vue'

export default {
  name: 'energy-list',
  props:['data'],

  components: {
    "list-component": ListComponent
  }

}

</script>

<style lang="css" scoped>
</style>
