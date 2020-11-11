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
        <div class="weather__wrap" v-if="data.main">
          <div class="location__box">
            <div class="date">{{ dateBuilder() }}</div>
            <div class="location">{{ data.name }}, {{ data.sys.country }}</div>
          </div>
          <div class="weather__box">
            <div class="temp">{{ Math.round(data.main.temp) }}°C</div>
            <div class="weather">{{ data.weather[0].description }}</div>
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
    dateBuilder () {
      let d = new Date()
      let months = this.$store.state.months
      let days = this.$store.state.days
      let day = days[d.getDay()]
      let date = d.getDate()
      let month = months[d.getMonth()]
      let year = d.getFullYear()

      return `${day} ${date}. ${month} ${year}`
    }
  }
}
</script>
<style>

</style>
