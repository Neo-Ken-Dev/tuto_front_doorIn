<template>
  <v-app>
    <v-simple-table
      fixed-header
      height="300px"
    >
      <template v-slot:default>
        <thead>
        <tr>
          <th class="text-left">
            Nom
          </th>
          <th class="text-left">
            Adresse
          </th>
          <th class="text-left">
            Code immeuble
          </th>
          <th class="text-left">
            code société
          </th>
        </tr>
        </thead>
        <tbody>
        <tr>
          <td>{{immeuble.name}}</td>
          <td>{{immeuble.address}}</td>
          <td>{{immeuble.code_im}}</td>
          <td>{{immeuble.code_soc}}</td>
        </tr>
        </tbody>
        <v-btn color="primary" nuxt :to="{ name: 'user-account'}">
          Retour
        </v-btn>
      </template>
    </v-simple-table>


  </v-app>
</template>

<script>
export default {

  data: () => ({
    immeuble: {}
  }),

  mounted () {
    this.$axios.get(`api/immeubles/${this.$route.params.id}`)
      .then((res) => {
        this.immeuble = res.data
      }).catch( (err) => {
      return this.$nuxt.error({  })
    })
  },
};
</script>

<style></style>
