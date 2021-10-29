<template>
  <v-app id="inspire">
    <v-main>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4>
            <v-card class="elevation-12">
              <v-toolbar dark color="primary">
                <v-toolbar-title>Formulaire de connexion</v-toolbar-title>
              </v-toolbar>
              <v-card-text>
                <v-form method="post">
                  <v-text-field
                    prepend-icon="mdi-account"
                    name="login"
                    label="Pseudo"
                    type="text"
                    v-model="formData.pseudo"
                  ></v-text-field>
                  <v-text-field
                    id="password"
                    prepend-icon="mdi-lock"
                    name="password"
                    label="Mot de passe"
                    type="password"
                    v-model="formData.password"
                  ></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="primary" type="submit" v-on:click="login">Se connecter</v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'Login',
  props: {

  },

  data () {
    return {
      formData : {
        pseudo: '',
        password: ''
      }
    }
  },

  methods: {
    async login() {
      try {
        await this.$auth.loginWith('local', {data: this.formData})
        await this.$router.push('/')
      } catch (error) {
        console.log("err :")
        console.log(error)
        console.log(error)
      }

      // this.$axios.$post('/api/auth/login', this.formData)
      //   .then(function (response) {
      //     console.log("user connected")
      //     console.log("response")
      //     this.$router.push('/')
      //   }).catch(function (err) {
      //     console.log("err :")
      //     console.log(err)
      //
      // })
    }
  },
};
</script>

<style></style>
