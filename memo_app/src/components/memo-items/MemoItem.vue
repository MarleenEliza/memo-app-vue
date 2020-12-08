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
        <span class="link-span">{{ link }}</span>
      </v-btn>
      <v-btn
        class="mx-2 deleteBtn"
        fab
        dark
        color="error"
        @click="removeMemo(id)"
      >
        <v-icon>mdi-trash-can</v-icon>
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  props: ["id", "title", "description", "link"],
  inject: ["removeMemo"],
};
</script>

<style scoped>
.v-card {
  display: grid;
  margin: 2rem;
  padding: 1rem;
}

.v-card .v-card__actions {
  display: contents;
  justify-content: space-between;
}

@media only screen and (min-width: 800px) {
  .v-card .v-card__actions {
    display: flex;
  }
}

/* Set links in the middle */
 a {
  display: block !important;
  padding: inherit !important;
}

.link-span {
  overflow: hidden !important;
  white-space: nowrap;
  text-overflow: ellipsis; 
}

.deleteBtn {
  justify-self: right;
}
</style>
