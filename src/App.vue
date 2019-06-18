<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <v-icon large color="red">fas fa-list</v-icon>
        <span class="font-weight-light">Api filter</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        flat
        href="https://github.com/vladkaryakin"
        target="_blank"
      >
        <span class="mr-2">Contact the author</span>
      </v-btn>
    </v-toolbar>
    <v-content>
      <MainComponent/>
    </v-content>
  </v-app>
</template>

<script>

import MainComponent from './components/MainComponent'

export default {
  name: 'App',
  components: {
    MainComponent
  },
  data () {
    return {
      
    }
  }
}
</script>

<style>
  
</style>