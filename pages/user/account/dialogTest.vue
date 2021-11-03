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
          v-for="item in accountsWithImmeuble"
          :key="item.id"
        >
          <td>{{ item.content}}</td>
          <td>{{ item.immeuble.address}}</td>
          <td >
            <v-btn
              color="primary lighten-2"
              dark
              @click="dialog = true; selectedImmeuble = item.immeuble"
            >
              Click Me
            </v-btn>
          </td>
        </tr>

        </tbody>
      </template>
    </v-simple-table>

    <Dialog :selectedIm="selectedImmeuble" @closeDialog="dialog = false" v-model="dialog"></Dialog>

  </v-app>
</template>

<script>
import Dialog from "../../../components/Dialog";
export default {
  components: {Dialog},
  data () {
    return {
      accountsWithImmeuble: {},
      dialog: false,
      selectedImmeuble: null,
    }
  },

  async fetch() {
    await this.$axios.$get(`api/user/${this.$store.state.auth.user.id}/accounts`)
    .then((res) => {
      this.accountsWithImmeuble = res.accounts
    }).catch( (err) => {
        return this.$nuxt.error({  })
      })
  },
};
</script>

<style></style>
