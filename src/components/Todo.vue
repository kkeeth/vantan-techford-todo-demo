<template>
  <div class="container">
    <h1>はじめてのTODOアプリ</h1>

    <div class="contents">
      <!-- タスクを追加のカード -->
      <add-todo />

      <!-- 完了済タスク -->
      <completed-todo />

      <!-- 未完了タスク -->
      <incomplete-todo :todo-list="todoList" />

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
  data() {
    return {
      todoList: [
        { title: '牛乳買ってくる', status: false },
        { title: '髪切る', status: false },
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
h1 {
  font-size: 1.5rem;
  font-weight: bold;
}

.container {
  display: flex;
  flex-direction: column;
}

.contents {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
}

.card {
  border: 1px solid #999;
  border-radius: 4px;
  max-width: 200px;
  padding: 10px;
  background-color: #fff;

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