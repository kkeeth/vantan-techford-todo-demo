<template>
  <div class="card">
    <div class="title">タスクを追加</div>
    <div class="contents-wrapper">
      <input type="text" placeholder="テキストを入力" />
      <v-button title="追加" />
    </div>
  </div>
</template>

<script>
import VButton from "./VButton.vue";

export default {
  name: "CompletedTodo",
  components: {
    VButton,
  },
};
</script>

<style scoped>
.contents-wrapper {
  margin-top: 12px;
}

.contents-wrapper input {
  border: 2px solid #999;
  border-radius: 8px;
  padding: 2px 0;
}
</style>
