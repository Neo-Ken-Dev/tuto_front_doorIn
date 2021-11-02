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
            Nom de l'immeuble
          </th>
          <th class="text-left">
            Plus d'infos
          </th>
        </tr>
        </thead>
        <tbody>
        <tr
          v-for="item in immeubles"
          :key="item.name"
        >
          <td>{{ item.name }}</td>
          <td>
            <v-btn color="primary" dark nuxt :to="{ name: 'user-immeuble-id', params: { id: item.id }}">
              <v-icon left dark>mdi-information-variant</v-icon>
                Plus d'infos
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
    immeubles: []
  }),
  async fetch() {
    this.immeubles = await this.$axios.$get(`api/user/${this.$store.state.auth.user.id}/immeubles`)
      .catch( (err) => {
        return this.$nuxt.error({  })
      })
  },
};
</script>

<style></style>
