<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <v-app>
    <v-app-bar color="primary darken-2" dark>
      <v-app-bar-title class="white--text">Web Scraping Portal</v-app-bar-title>
      <v-spacer></v-spacer>

      <v-btn icon to="/websites">
        <v-icon>mdi-format-list-bulleted</v-icon>
      </v-btn>

      <v-btn icon to="/website/new">
        <v-icon>mdi-plus-circle-outline</v-icon>
      </v-btn>

      <v-btn icon to="/logout">
        <v-icon>mdi-exit-to-app</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>

    <v-footer color="primary darken-2" app>
      <span class="white--text">&copy; 2023 IAW - UNLP</span>
    </v-footer>
  </v-app>
</template>

<style scoped>
  .white--text {
    color: white;
  }

  .primary.darken-2 {
    background-color: #1976D2; /* Color primario con tono oscuro */
  }

  .primary.darken-2--text {
    color: #1976D2; /* Texto en el color primario con tono oscuro */
  }

  .primary.lighten-2 {
    background-color: #64B5F6; /* Color primario con tono claro */
  }

  .primary.lighten-2--text {
    color: #64B5F6; /* Texto en el color primario con tono claro */
  }

  .accent-4 {
    background-color: #FFC107; /* Color de acento */
  }

  .accent-4--text {
    color: #FFC107; /* Texto en el color de acento */
  }

  .footer-color {
    background-color: #1976D2; /* Color del pie de página */
    color: white; /* Texto en el pie de página */
    text-align: center;
    padding: 10px 0;
  }
</style>

