<template>
  <div class="NotFound">
    <v-container>
      <v-layout row wrap>
        <v-flex xs12>
          <v-card height="400" color="transparent" flat>
            <div class="display-3 mt-5">Page non trouvée.</div>
            <div class="grey--text lighten-5">
              La page à laquelle vous essayez d'accéder n'existe pas !
            </div>
            <div class="paragraph-text mt-2">
              <br />
              <br />Essayez de revenir à la page d'accueil et de répéter votre action. Ou,
              contactez le service d'assistance pour obtenir de l'aide.
            </div>
          </v-card>
          <v-btn color="primary" dark nuxt :to="{ name: 'index'}">
            Retour à la page d'accueil
          </v-btn>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
export default {

  props: {
    error: {
      type: Object,
      default: null
    }
  },
  data () {
    return {
      pageNotFound: '404 Not Found',
      otherError: 'Une erreur est survenue'
    }
  },
  head () {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError
    return {title}
  }
}
</script>

<style>
.paragraph-text {
  font-size: 18px;
}
</style>
