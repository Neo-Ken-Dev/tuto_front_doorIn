<template>
  <v-toolbar>
    <v-toolbar-title>
      <router-link to="/" tag="span" style="cursor: pointer">
        {{ appTitle }}
      </router-link>
    </v-toolbar-title>
    <v-spacer></v-spacer>

    <v-toolbar-items v-if="isAuthenticated">
      <v-menu offset-y transition="slide-x-transition">
        <template v-slot:activator="{on}">
          <v-btn
            color="primary"
            dark
            v-on="on"
          >
            Menu
          </v-btn>
        </template>
        <v-list>
          <v-list-item>
            <v-icon left color="indigo">mdi-account</v-icon>
            <NuxtLink :to="{name: 'myProfile'}">
              Votre profile
            </NuxtLink>
          </v-list-item>
          <v-list-item>
            <v-icon left color="indigo">mdi-account-arrow-right</v-icon>
            <NuxtLink :to="{name: 'user-account'}">
              Vos comptes
            </NuxtLink>
          </v-list-item>
          <v-list-item>
            <v-icon left color="indigo">mdi-account-arrow-right</v-icon>
            <NuxtLink :to="{name: 'user-account-dialogTest'}">
              Vos comptes 2
            </NuxtLink>
          </v-list-item>
          <v-list-item>
            <v-icon left color="indigo">mdi-office-building-cog</v-icon>
            <NuxtLink to="/user/immeuble">
              Vos immeubles
            </NuxtLink>
          </v-list-item>

          <v-list-item>
            <v-icon left color="indigo">mdi-office-building-cog</v-icon>
            <v-btn color="primary" type="submit" v-on:click="logout">Se déconnecter</v-btn>
          </v-list-item>

        </v-list>
      </v-menu>

    </v-toolbar-items>

    <v-toolbar-items v-else>
      <v-btn
        text
        v-for="item in menuItems"
        :key="item.title"
        :to="item.path">
        <v-icon left color="indigo">{{ item.icon }}</v-icon>
        {{ item.title }}
      </v-btn>
    </v-toolbar-items>

  </v-toolbar>
</template>

<script>
import { mapGetters } from 'vuex'
export default {
  data () {
    return {
      appTitle: 'Tuto_Front_Door-in',

      menuItems: [
        {title: 'S\'enregistrer', path: '/register', icon: 'mdi-account-plus'},
        {title: 'Se connecter', path: '/login', icon: 'mdi-account'}
      ],
    }
  },

  computed: {
    ...mapGetters(['isAuthenticated', 'loggedInUser']),

    // isAuthenticated() {
    //   return this.$store.getters.isAuthenticated;  // it check if user isAuthenticated
    // }
  },

  methods: {
    async logout() {
      try {
        await this.$auth.logout('local')
      } catch (error) {
        this.errorMessage = "Identifiant incorrect."
      }
    }
  },
}
</script>
