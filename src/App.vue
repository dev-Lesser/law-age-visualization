<template>
  <v-app>
    <v-app-bar
      app
      color="grey darken-3"
      dark
    >
      
    </v-app-bar>

    <v-main>
      <law-table />
    </v-main>
  </v-app>
</template>

<script>
import LawTable from './components/LawTable';
import lawData from '@/assets/data.json'
export default {
  name: 'App',

  components: {
    LawTable,
  },

  data: () => ({
    //
  }),
  created(){
    this.$store.state.lawData = lawData;
  }
};
</script>
