<template>
  <v-app>
    <v-main>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4>

            <v-card class="px-4">
              <v-card-text>
                <v-alert v-show="errorMessage"
                         border="left"
                         type="error"
                         icon="mdi-cloud-alert"
                >
                  {{ errorMessage }}
                </v-alert>

                <v-form >
                  <v-row>
                    <v-col cols="12" sm="6" md="6">
                      <v-text-field v-model="formData.pseudo" label="Pseuso" required></v-text-field>
                    </v-col>

                    <v-col cols="12">
                      <v-text-field v-model="formData.bio" label="Biographie" ></v-text-field>
                    </v-col>

                    <v-col cols="12">
                      <v-text-field v-model="formData.phone" label="Telephone" ></v-text-field>
                    </v-col>

                    <v-col cols="12">
                      <v-text-field v-model="formData.address" label="Votre adresse" ></v-text-field>
                    </v-col>

                    <v-col cols="12">
                      <v-text-field v-model="formData.city" label="Ville" ></v-text-field>
                    </v-col>

                    <v-col cols="12">
                      <v-text-field v-model="formData.zipcode" label="Code postal" ></v-text-field>
                    </v-col>

                    <v-col cols="12">
                      <v-text-field v-model="formData.country" label="Pays" ></v-text-field>
                    </v-col>

                    <v-col cols="12">
                      <v-text-field v-model="formData.password" label="Mot de Passe" type="password"></v-text-field>
                    </v-col>

                    <v-spacer></v-spacer>
                  </v-row>
                </v-form>
              </v-card-text>

              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="primary" type="submit" v-on:click="register">S'enregistrer</v-btn>
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
  name: 'Register',

  data () {
    return {
      errorMessage: null,
      formData : {
        pseudo: '',
        bio:'',
        phone:'',
        address:'',
        city:'',
        zipcode:'',
        country:'',
        password: ''
      }
    }
  },

  methods: {
    async register() {
      try {
        await this.$axios.post('api/auth/register', this.formData)
        await this.$auth.loginWith('local', {
          data: {
            pseudo: this.formData.pseudo,
            password: this.formData.password
          },
        })
        await this.$router.push('/')
      } catch (error) {
        this.errorMessage = "Une erreur s'est produite"
      }
    }
  },
};
</script>

<style></style>
