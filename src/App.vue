<template>
  <v-app>
    
    <Sidebar />
    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
import Sidebar from './components/Sidebar.vue';
export default {
  name: 'App',

  components: {
    Sidebar,
  },

  data: () => ({
    //
  }),
};
</script>
