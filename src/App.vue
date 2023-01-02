<template>
  <v-app>
    <v-app-bar
      app
     
      dark
      style="background-color:rgb(53,58,63)"
     
    >
      <div class="d-flex align-center topLogo">
     

    
      </div>

      <v-spacer></v-spacer>

      <v-btn
      depressed
      color="primary"
    >
      login
    </v-btn>
    </v-app-bar>

    <v-main>
      <DashboardHome/>
    </v-main>
  </v-app>
</template>

<script>

import DashboardHome from './components/DashboardHome'

export default {
  name: 'App',

  components: {
   
    DashboardHome
  },

  data: () => ({
    //
  }),
};
</script>
<style scoped>
.topLogo{
  background-image: url("./assets/logo2.png");
  background-size: contain;
  background-position: center;
  height: 4rem;
 
  width: 6rem;
  }
</style>