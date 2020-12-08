<template>
  <v-app>
    <div>
      <v-btn
        width="100px"
        class="mx-2 my-2"
        text
        :color="setMemoButtonColor('stored-memo')"
        @click="setSelectedTab('stored-memo')"
      >
        <v-icon class="mr-2" light>mdi-view-list</v-icon>
        View
      </v-btn>
      <v-btn
        text
        width="100px"
        class="mx-2 my-2"
        :color="setMemoButtonColor('add-memo')"
        @click="setSelectedTab('add-memo')"
      >
        <v-icon class="mr-2">mdi-note-plus </v-icon>
        Add
      </v-btn>
      <v-divider></v-divider>
    </div>
    <keep-alive>
      <component :is="selectedTab"></component>
    </keep-alive>
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
      addMemo: this.addMemo,
      removeMemo: this.removeMemo,
    };
  },
  methods: {
    // Set the tab and colors of buttons based on wheter VIEW or ADD
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    setMemoButtonColor(type) {
      return this.selectedTab === type ? "primary" : "grey darken-2";
    },

    // 
    addMemo(title, description, url) {
      const newMemo = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url,
      };
      this.storedMemo.unshift(newMemo);
      this.selectedTab = "stored-memo";
    },
    removeMemo(memoId) {
      const memoIndex = this.storedMemo.findIndex(memo => memo.id === memoId);
      this.storedMemo.splice(memoIndex, 1);
    }
  },
};
</script>