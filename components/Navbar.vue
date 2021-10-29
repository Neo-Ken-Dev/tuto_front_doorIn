<template>
  <v-toolbar app>
    <v-toolbar-title>
      <router-link to="/" tag="span" style="cursor: pointer">
        {{ appTitle }}
      </router-link>
    </v-toolbar-title>
    <v-spacer></v-spacer>
    <v-toolbar-items class="hidden-xs-only">
      <v-btn
        flat
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

export default {

  data () {
    return {
      appTitle: 'Tuto_Front_Door-in',
      menuItems: [
        { title: 'S\'enregistrer', path: '/register', icon: 'mdi-account-plus' },
        { title: 'Se connecter', path: '/login', icon: 'mdi-account' }
      ]
    }
  }
}
</script>
