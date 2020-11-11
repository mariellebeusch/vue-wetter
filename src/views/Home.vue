<template>
  <div class="home">
      <input v-model="forecast">
      <br>
      {{ forecast }}

  </div>
</template>

<script>

export default {
  name: 'Home',
  data () {
    return {
      city: '',
      forecast: '20 Grad, Sonne'
    }
  },
  methods: {
    fetchWeather () {
      // fetch api
      // später axios

    }
  }
}
</script>
