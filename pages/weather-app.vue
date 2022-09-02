<template>
  <v-container>
    <h1 class="display-1 text-center">Weather APP</h1>
    <!-- <v-layout> -->
    <v-flex xs12>
      <v-card color="blue-grey darken-2" dark>
        <v-card-text>
          <v-layout  v-if="weather.weather" justify-center>
      
            <v-flex class="text-center">
              <h4>wind & Pressure</h4>
              <h3 class="headline">
                Wind :{{ weather.wind.speed }} m/s ({{
                  weather.wind.deg
                }}
                &#176;C)
              </h3>
              <h3 class="headline mt-4">
                Humidity :{{ weather.main.humidity }}%
              </h3>
              <h3 class="headline mt-4">
                Pressure:{{ weather.main.pressure }} hPa
              </h3>
            </v-flex>
                  <v-flex class="text-center">
              <h4>Temprature</h4>
              <h1 class="display-1">{{ weather.name }}</h1>
              <img :src="icon" alt="" />
              <p>
                <span class="display-1"
                  >{{ Math.round(weather.main.temp - 273) }} &#176;C</span
                >
                <span class="caption ml-4">{{
                  weather.weather[0].description
                }}</span>
              </p>
            </v-flex>
            <v-flex class="text-center">
              <h4>Others :</h4>
              <h3 class="headline mt-4">Max Temp :{{ Math.round(weather.main.temp_max - 273) }}&deg;C</h3>
              <h3 class="headline mt-4">Min Temp :{{ Math.round(weather.main.temp_min - 273) }}&deg;C</h3>
            </v-flex>
          </v-layout>
        </v-card-text>
      </v-card>
    </v-flex>
    <v-flex xs12 class="mt-4">
      <v-text-field
        v-model="city"
        label="Enter city Name"
        outlined
      ></v-text-field>
    </v-flex>
    <v-btn color="success" @click="getInformation">Get information</v-btn>
    <!-- </v-layout> -->
  </v-container>
</template>

<script>
export default {

  data() {
    return {
      APIKEY: '842dead290490e388c49c30c22b83e95',
      city: 'London',
        weather: {},
    }
  },
    computed: {
    icon() {
      return this.weather.weather[0].icon
        ? `https://api.openweathermap.org/img/w/${this.weather.weather[0].icon}.png`
        : ''
    },
  },
  created() {
    this.getInformation()
  },
 

  methods: {
    getInformation() {
      this.$axios
        .$get(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=2ea2b584fd5affa6a537807ddb96524b`
        )
        .then((res) => {
          console.log(res)
          this.weather = res
        })
    },
  },
}
</script>