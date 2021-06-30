<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
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

export default {
  name: 'App',

  components: {
    LawTable,
  },

  data: () => ({
    //
  }),
};
</script>
