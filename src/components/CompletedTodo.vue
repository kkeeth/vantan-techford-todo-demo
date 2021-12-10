<template>
  <div class="card">
    <div class="title">完了済みタスク</div>
    <div class="contents-wrapper">
      <ul class="todo-list">
        <input type="checkbox" value="" />
        <v-button title="削除" />
      </ul>
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
  text-align: left;
  padding-left: 20px;
}
</style>
