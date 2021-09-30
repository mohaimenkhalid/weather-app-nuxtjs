<template>
  <v-app>
    <v-content>
      <v-toolbar color="indigo dark">
        <v-app-bar-nav-icon></v-app-bar-nav-icon>
        <v-toolbar-title>Weather App</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-sm-and-down">
          <v-btn>
            <n-link to="/">Home</n-link>
          </v-btn>
        </v-toolbar-items>
      </v-toolbar>
    </v-content>
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
