<template>
  <v-app>
    <v-app-bar app class="app-bar">
      <div class="header-bar">
        <h1 class="header-title">Admin Panel</h1>
      </div>
      <v-spacer></v-spacer>
    </v-app-bar>

    <v-main>
      <admin-panel/>
    </v-main>
  </v-app>
</template>

<script>
import AdminPanel from './components/admin-panel.vue';

export default {
  name: "App",

  components: {
    AdminPanel
  },

  data: () => ({
    //
  })
};
</script>
<style scoped>
.app-bar {
    background: #3A1C71;
    background: -webkit-linear-gradient(90deg, #6a0000, #010156);
    background: linear-gradient(90deg, #6a0000, #010156);
}
.header-title {
  color: white;
  text-align: center;
}
.header-bar {
  width: 100%;
  text-align: center;
}
</style>