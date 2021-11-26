<template>
  <div>
    <h1>はじめてのTODOアプリ</h1>

    <div>
      <!-- タスクを追加のカード -->
      <add-todo />

      <!-- 完了済タスク -->
      <completed-todo />

      <!-- 未完了タスク -->
      <incomplete-todo />

      <!-- すべてのタスク -->
      <all-todo />

    </div>
  </div>
</template>

<script>
import AddTodo from './AddTodo.vue'
import CompletedTodo from './CompletedTodo.vue'
import IncompleteTodo from './IncompleteTodo.vue'
import AllTodo from './AllTodo.vue'

export default {
  name: 'Todo',
  components: {
    AddTodo,
    CompletedTodo,
    IncompleteTodo,
    AllTodo,
  },
}
</script>

<style lang="scss" scoped>
.card {
  border: 1px solid #999;
  border-radius: 4px;
  max-width: 200px;
  padding: 10px;

  /* & + & {
    margin-top: 20px;
  } */

  /* .contents-wrapper {
        display: flex;
        justify-content: center;
  } */
}

.card + .card {
  margin-top: 20px;
}

.contents-wrapper {
  display: flex;
  justify-content: center;
}
</style>