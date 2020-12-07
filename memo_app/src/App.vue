<template>
  <v-app>
    <v-list>
      <memo-item
        v-for="memo in storedMemo"
        :key="memo.id"
        :title="memo.title"
        :description="memo.description"
        :link="memo.link"
      ></memo-item>
    </v-list>
  </v-app>
</template>

<script>
import MemoItem from "./components/memo-items/MemoItem.vue";

export default {
  components: {
    MemoItem: MemoItem,
  },
  data() {
    return {
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
};
</script>

#global style
<style>
@import url("https://fonts.googleapis.com/css2?family=PT+Sans&display=swap");

html {
  font-family: "PT Sans", sans-serif;
  box-sizing: border-box;
}

body{
  margin: 0;
}

</style>
