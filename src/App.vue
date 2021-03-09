<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <h1>Budget Calculator</h1>
      </div>
    </v-app-bar>

    <v-main class="grey lighten-2">
      <main-dashboard />
    </v-main>
  </v-app>
</template>

<script>
import mainDashboard from "./components/mainDashboard.vue";

export default {
  components: {
    mainDashboard,
  },
};
</script>

