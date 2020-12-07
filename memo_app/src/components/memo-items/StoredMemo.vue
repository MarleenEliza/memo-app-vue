<template>
    <v-list>
      <memo-item
        v-for="memo in memos"
        :key="memo.id"
        :title="memo.title"
        :description="memo.description"
        :link="memo.link"
      ></memo-item>
    </v-list>
</template>

<script>
import MemoItem from './MemoItem.vue';

export default {
    inject: ['memos'],
    components: {
      MemoItem
    }
}
</script>