<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <v-icon large color="red">fas fa-list</v-icon>
        <span class="font-weight-light">Create your own TODOS list</span>
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
      <TodosComponent/>
    </v-content>
  </v-app>
</template>

<script>

import TodosComponent from './components/TodosComponent'

export default {
  name: 'App',
  components: {
    TodosComponent
  },
  data () {
    return {
      
    }
  }
}
</script>

<style>
  
</style>