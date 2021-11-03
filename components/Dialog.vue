<template>
  <v-dialog
    v-model="inputVal"
    width="500"
  >
    <v-card>
      <v-card-title class="text-h5 grey lighten-2">
        Immeuble informations
      </v-card-title>

      <v-card-text v-if="selectedIm"> Adresse:
        {{ selectedIm.address }}
      </v-card-text>
      <v-card-text v-if="selectedIm"> Code immeuble:
        {{ selectedIm.code_im }}
      </v-card-text>
      <v-card-text v-if="selectedIm"> Code société:
        {{ selectedIm.code_soc }}
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
