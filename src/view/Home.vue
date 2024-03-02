
<template>
  <v-app>
      <Navbar/>
  </v-app>

</template>

<script>
  import Navbar from '../components/Navbar.vue'
  export default{
      name: 'Home',
      components :{
          Navbar, 
      }
  }
</script>


<style>
/* Helper classes */
.bg-basil {
  background-color: #FFFBE6 !important;
}
.text-basil {
  color: #356859 !important;
}
</style>