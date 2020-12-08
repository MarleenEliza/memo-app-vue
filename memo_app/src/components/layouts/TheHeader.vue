<template>
  <v-footer
  class="mb-5"
  padless
  >
    <v-card
      flat
      tile
      width="100%"
      class="blue-grey lighten-4 white--text text-left">
      <v-card-title primary-title class="light-blue darken-4 justify-center">
        <h1>{{ title }} </h1>
      </v-card-title>

      <v-card-text class="py-2">
        {{ new Date().getFullYear() }} — Marleen Dijkman
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<script>
export default {
  props: ["title"],
};
</script>