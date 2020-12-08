<template>
  <v-card>
    <v-form ref="form" v-model="valid" lazy-validation>
      <v-text-field
        outlined
        v-model="title"
        :rules="titleRules"
        label="Memo-Title"
        ref="title"
        required
      ></v-text-field>

      <v-textarea
        outlined
        v-model="description"
        :rules="descriptionRules"
        ref="description"
        label="Description"
      ></v-textarea>

      <v-btn :disabled="!valid" color="success" class="mr-4" @click="validate">
        Validate
      </v-btn>
    </v-form>
  </v-card>
</template>

<script>
export default {
  inject: ['addMemo'],
  data() {
    return {
      valid: true,
      title: "",
      titleRules: [
        (v) => !!v || "Name is required",
        (v) => (v && v.length <= 10) || "Name must be less than 10 characters",
      ],
      description: "",
      descriptionRules: [
        (v) =>
          (v && v.length <= 200) ||
          v === "" ||
          "Description must be less than 200 characters",
      ],
    };
  },

  methods: {
    validate() {
      this.$refs.form.validate();

      const enteredTitle = this.$refs.title.value;
      const enteredDescription = this.$refs.description.value;
      const enteredUrl = "www.google.nl"

      this.addMemo(enteredTitle, enteredDescription, enteredUrl);
    },
  },
};
</script>

<style scoped>
.v-card {
  display: grid;
  margin: 2rem;
  padding: 1rem;
}
</style>