<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <h1 class="display-2 text-center mb-2">Weather page</h1>
      </v-col>
      <v-col cols="12">
        <v-card
          color="blue-grey darken-1"
          dark
        >
          <v-row>
            <v-col cols="4" xs-12>
              <v-card-text class="text-center">
                <h4>Temperature</h4>
                <h1 class="display-1">{{weather.name}}</h1>
                <img :src="icon" alt="icon">
                <h1 class="display-1">{{ temp }} &deg; C</h1>
                <span class="caption ml-4">{{ weather.weather[0].description}}</span>
              </v-card-text>
            </v-col>
            <v-col cols="4">
              <v-card-text class="text-center">
                <h3 class="headline">Wind & Pressure:</h3>
                <h5 class="heading">{{weather.wind.speed}} m/s ({{weather.wind.deg}})</h5>
                <h3 class="headline mt-4">Humidity: {{weather.main.humidity}} %</h3>
                <h3 class="headline mt-4">Pressure: {{weather.main.pressure}} hpa</h3>
              </v-card-text>
            </v-col>
            <v-col cols="4">
              <v-card-text class="text-center">
                <h3 class="headline">Other:</h3>
                <h3 class="mt-4">Max Temperature: {{Math.round(weather.main.temp_max - 273)}} &deg; c</h3>
                <h3 class="mt-4">Min Temperature: {{Math.round(weather.main.temp_min - 273)}} &deg; c</h3>
              </v-card-text>
            </v-col>
          </v-row>
        </v-card>
      </v-col>
      <v-col cols="12">
        <v-form @submit.prevent="getWeatherInfo">
          <v-text-field
            v-model="city"
            solo
            label="Enter Your City"
            clearable
          ></v-text-field>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      city: 'London',
      weather: {}
    }
  },
  asyncData({$axios}) {
    return $axios.$get(`https://api.openweathermap.org/data/2.5/weather?q=London&appid=${process.env.weatherAppKey}`)
    .then(res => {
      return {
        weather: res
      }
    })
  },
  created() {
    this.getWeatherInfo();
  },
  computed: {
    icon() {
      return `https://openweathermap.org/img/w/${this.weather.weather[0].icon}.png`;
    },

    temp() {
      return Math.round(this.weather.main.temp - 273.15);
    }
  },
  methods: {
    getWeatherInfo() {
      this.$axios.$get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${process.env.weatherAppKey}`)
        .then(res => {
          this.weather = res;
          console.log(res)
        })
        .catch()
    }
  }
}

</script>

<style>

</style>
