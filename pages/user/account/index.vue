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
            Contenu
          </th>
          <th class="text-left">
            Plus d'infos
          </th>
        </tr>
        </thead>
        <tbody>
        <tr
          v-for="item in accounts"
          :key="item.content"
        >
          <td>{{ item.content }}</td>
          <td>
            <v-btn color="primary" dark nuxt :to="{ name: 'user-account-immeuble-id', params: { id: item.id }}">
              <v-icon left dark>mdi-information-variant</v-icon>
              Informations sur l'immeuble
            </v-btn>
          </td>
        </tr>
        </tbody>
      </template>
    </v-simple-table>

  </v-app>
</template>

<script>
export default {

  data: () => ({
    accounts: []
  }),
  async fetch() {
    this.accounts = await this.$axios.$get(`api/user/${this.$store.state.auth.user.id}/accounts`)
      .catch( (err) => {
        return this.$nuxt.error({  })
      })
  },
};
</script>

<style></style>
