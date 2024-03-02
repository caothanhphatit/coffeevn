<template>
    <v-app>
          <Homecard @navigateToTab="navigateToTab"></Homecard>
    </v-app>
  </template>
  
<script>
import Homecard from './Homecard.vue'
export default {
  components :{
    Homecard, 
      },
    methods: {
    navigateToTab(tabIndex) {
      this.$emit('navigateToTab', tabIndex);
    }
  }
  }
</script>