<template>
  <v-app>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <v-card>
          <v-card-text>
            <v-text-field
              v-model="formData.pseudo"
              label="Pseudo"></v-text-field>
            <v-text-field
              v-model="formData.bio"
              label="Biographie"></v-text-field>
            <v-text-field
              v-model="formData.phone"
              label="Téléphone"></v-text-field>
            <v-text-field
              v-model="formData.address"
              label="Adresse"></v-text-field>
            <v-text-field
              v-model="formData.city"
              label="Ville"></v-text-field>
            <v-text-field
              v-model="formData.zipcode"
              label="Code postal"></v-text-field>
            <v-text-field
              v-model="formData.country"
              label="Pays"></v-text-field>
          </v-card-text>
          <v-card-actions>
            <v-btn color="primary" @click="updateUser">
              <v-icon left dark>mdi-check</v-icon>
              Sauvegarder
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-app>
</template>

<script>

export default {
  name: 'MyProfile',

 mounted: function () {
   this.formData.pseudo = this.user.pseudo;
   this.formData.bio = this.user.bio;
   this.formData.phone = this.user.phone;
   this.formData.address = this.user.address;
   this.formData.city = this.user.city;
   this.formData.zipcode = this.user.zipcode;
   this.formData.country = this.user.country;
 },
  data () {
    return {
      user: this.$auth.user,
      formData : {
        pseudo: '',
        bio:'',
        phone:'',
        address:'',
        city:'',
        zipcode:'',
        country:'',
      }
    }
  },

  methods: {
    async updateUser() {
      const url = `api/users/${this.$store.state.auth.user.id}`
      console.log(this.formData)
      console.log(url)
        await this.$axios.$put(url, this.formData)
      .then(res => {
        console.log(res)

      })
      .catch(error => {
        console.log(error)
      })
    }
  }
};
</script>
