<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-text-field
            v-model="query"
            label="Ort eingeben..."
            clearable
            @keypress="fetchWeather"
        ></v-text-field>
      </v-col>
      <v-col>
        <div class="weather__wrap">
          <div class="location__box">
            <div class="date">Mittwoch, 11. November 2020</div>
            <div class="location">Chur, CH</div>
          </div>
          <div class="weather__box">
            <div class="temp">6°C</div>
            <div class="weather">klar</div>
          </div>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'WeatherWidget',
  computed: {},
  data () {
    return {
      api_key: process.env.VUE_APP_API_KEY,
      url_base: process.env.VUE_APP_API_BASE,
      query: '',
      data: {}
    }
  },
  methods: {
    fetchWeather (e) {
      if (e.key === 'Enter') {
        fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
          .then(res => {
            return res.json()
          })
          .then(this.setResults)
      }
    },
    setResults (results) {
      this.data = results
    },
  }
}
</script>
<style>

</style>
