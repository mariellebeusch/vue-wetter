<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-text-field
            v-model="query"
            label="Ort eingeben..."
            clearable
        ></v-text-field>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'WeatherWidget',
  computed: {

  },
  data () {
    return {
      query: '',
    }
  }
}
</script>
<style>

</style>
