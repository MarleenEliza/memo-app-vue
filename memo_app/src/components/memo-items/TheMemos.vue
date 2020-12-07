<template>
  <v-app>
    <div>
      <v-btn
        width="100px"
        class="mx-2 my-2"
        color="success"
        @click="setSelectedTab('stored-memo')"
      >
        <v-icon class="mr-2" light>mdi-view-list</v-icon>
        View
      </v-btn>
      <v-btn
        width="100px"
        class="mx-2 my-2"
        color="primary"
        @click="setSelectedTab('add-memo')"
      >
        <v-icon class="mr-2">mdi-note-plus </v-icon>
        Add
      </v-btn>
      <v-divider></v-divider>
    </div>
    <component :is="selectedTab"></component>
  </v-app>
</template>

<script>
import StoredMemo from "./StoredMemo.vue";
import AddMemo from "./AddMemo.vue";

export default {
  components: {
    StoredMemo,
    AddMemo,
  },
  data() {
    return {
      selectedTab: "stored-memos",
      storedMemo: [
        {
          id: "1",
          title: "Memo 1",
          description: "You should do this!",
          link: "https://github.com",
        },
        {
          id: "2",
          title: "Memo 2",
          description: "You should do this too!",
          link: "https://google.com",
        },
      ],
    };
  },
  provide() {
    return {
      memos: this.storedMemo,
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
  },
};
</script>