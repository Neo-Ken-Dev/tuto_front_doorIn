<template>
  <v-dialog
    v-model="inputVal"
    width="500"
  >
    <v-card>
      <v-card-title class="text-h5 grey lighten-2">
        Immeuble informations
      </v-card-title>

      <v-card-text v-if="selectedIm">
        {{ selectedIm.address }}
      </v-card-text>
      <v-divider></v-divider>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn
          color="primary"
          text
          @click='closeDialog()'
        >
          Retour
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  //la prop 'value' fait automatiquement le lien avec le v-model
  props: ['selectedIm', 'value'],

  methods: {
    closeDialog() {
      this.$emit('closeDialog');
    }
  },

  computed: {
    inputVal: {
      get() {
        return this.value;
      },
      set(val) {
        this.$emit('input', val);
      }
    }
  }
}

</script>
