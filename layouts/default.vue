<template>
  <v-app>
    <v-main>
      <v-toolbar color="indigo" dark>
        <v-app-bar-nav-icon></v-app-bar-nav-icon>
        <v-toolbar-title class="text--white">
          <n-link to="/">Nuxt JS App</n-link>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-sm-and-down">
          <v-btn class="transparent">
            <n-link to="/weather-app">
              Weather App
            </n-link>
          </v-btn>
        </v-toolbar-items>
      </v-toolbar>
      <nuxt />
    </v-main>
  </v-app>
</template>

<script>

export default {
  data () {
    return {

    }
  }
}
</script>

<style>
a {
  color: #ffffff !important;
  text-decoration: none;
}
</style>
