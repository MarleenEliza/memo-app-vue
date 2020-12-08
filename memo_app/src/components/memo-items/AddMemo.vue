<template>
  <v-card>
    <v-form ref="form" v-model="valid">
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

      <v-text-field
        outlined
        v-model="url"
        :rules="urlRules"
        label="URL"
        ref="url"
      ></v-text-field>

      <v-btn :disabled="!valid" color="success" class="mr-4" @click="validate">
        Add Memo
      </v-btn>
    </v-form>
  </v-card>
</template>

<script>
export default {
  inject: ["addMemo"],
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
      url: "",
      urlRules: [
        (v) =>
          v === "" ||
          /^(?:([A-Za-z]+):)?(\/{0,3})([0-9.\-A-Za-z]+)(?::(\d+))?(?:\/([^?#]*))?(?:\?([^#]*))?(?:#(.*))?$/.test(v) || "URL must be valid",
      ],
    };
  },

  methods: {
    validate() {
      this.$refs.form.validate();

      const enteredTitle = this.$refs.title.value;
      const enteredDescription = this.$refs.description.value;
      const enteredUrl = this.$refs.url.value;

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