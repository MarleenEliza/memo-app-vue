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
      selectedTab: "stored-memo",
      storedMemo: [
         {
          id: "1",
          title: "Add functions",
          description: "Still need to add edit function, maybe filter too　編集・フィルター昨日追加要",
          link: "https://v2.vuetifyjs.com/en/components/data-tables/",
        },
        {
          id: "2",
          title: "Project Code check",
          description: "Take a look at the code of this Project!　コードをご確認してください！",
          link: "https://github.com/MarleenEliza/memo-app-vue/tree/main/memo_app",
        },
        {
          id: "3",
          title: "Excercise Check JS",
          description: "See my self-study excercises on Javascript!　　 独学でしているJavascriptの練習問題をご確認ください！",
          link: "https://exercism.io/profiles/MarleenEliza",
        },
        {
          id: "4",
          title: "Excercise Check Python",
          description: "See my self-study excercises on Python! 　　独学でしているPythonの練習問題をご確認ください！",
          link: "https://www.hackerrank.com/marleeneliz4?hr_r=1",
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
      const memoIndex = this.storedMemo.findIndex((memo) => memo.id === memoId);
      this.storedMemo.splice(memoIndex, 1);
    },
  },
};
</script>