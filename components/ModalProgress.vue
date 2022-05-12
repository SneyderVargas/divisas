<template>
  <v-dialog v-model="dialog" persistent max-width="500px">
    <!--<v-btn color="primary" dark slot="activator">Open Dialog</v-btn>!-->
    <v-card>
      <v-card-title class="enter">
        <span class="headline">Cargando...</span>
      </v-card-title>
      <v-divider></v-divider>
      <v-card-text class="text-xs-center">
        <v-container grid-list-md>
          <v-layout wrap>
            <v-flex xs12>
              <v-progress-circular
                indeterminate
                :size="70"
                :width="7"
                color="purple"
              ></v-progress-circular>
            </v-flex>
          </v-layout>
        </v-container>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  data: () => ({}),
  computed: {
    dialog: {
      get() {
          return this.$store.state.progress;
      }
    },
  },
};
</script>

<style>
</style>