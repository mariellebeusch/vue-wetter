<template>
  <v-app>
    <v-app-bar
      app
      color="grey"
      dark
    >
      <div>
        Wetter App
      </div>
    </v-app-bar>

    <v-main>
      <weather/>
    </v-main>
  </v-app>
</template>

<script>
import Weather from '@/components/Weather'

export default {
  name: 'App',

  components: {
    Weather,
  },

  data: () => ({
    //
  }),
};
</script>
