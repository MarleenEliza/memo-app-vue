<template>
  <v-card>
    <v-card-title>{{ title }}</v-card-title>
    <v-card-text>
      <p>{{ description }}</p>
    </v-card-text>
    <v-card-actions>
        <v-btn
          color="light-blue darken-3"
          text
          :href="link"
        >
          {{ link }}
        </v-btn>
      <v-btn 
      class="mx-2" 
      fab 
      dark 
      color="error"
      @click="removeMemo(id)">
        <v-icon>mdi-trash-can</v-icon>
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  props: ["id","title", "description", "link"],
  inject: ['removeMemo'],
};
</script>

<style scoped>
.v-card {
  display: grid;
  margin: 2rem;
  padding: 1rem;
}

.v-card .v-card__actions{
  display: flex;
  justify-content: space-between;
}
</style>
