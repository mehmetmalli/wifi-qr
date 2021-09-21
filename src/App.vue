<template>
  <v-app>
    <Header/>
    <Main/>
  </v-app>
</template>

<script>
import Header from './components/Header.vue'
import Main from './views/Main.vue'

export default {
  name: "App",
  components: {
    Header,
    Main
  }
};
</script>
