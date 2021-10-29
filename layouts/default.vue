<template>
  <v-app dark>

    <Navbar></Navbar>

    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Navbar from "../components/Navbar";
export default {
  components: {Navbar},
  data () {
    return {

    }
  }
}
</script>
