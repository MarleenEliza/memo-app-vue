<template>
  <v-app>
    <the-header title="Memo It!"></the-header>
    <the-memos></the-memos>

  </v-app>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheMemos from './components/memo-items/TheMemos.vue';

export default {
  components: {
    TheHeader,
    TheMemos,
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

body {
  margin: 0;
}

</style>
