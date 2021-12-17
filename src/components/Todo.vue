<template>
  <div class="container">
    <h1>はじめてのTODOアプリ</h1>

    <div class="contents">
      <!-- タスクを追加のカード -->
      <add-todo @addTodo="addNewTodo" />

      <!-- 完了済タスク -->
      <completed-todo
        :todo-list="completedTodoList"
        @deleteTodo="deleteTodo"
        @changeStatus="changeStatus"
      />

      <!-- 未完了タスク -->
      <incomplete-todo
        :todo-list="inCompletedTodoList"
        @deleteTodo="deleteTodo"
        @changeStatus="changeStatus"
      />

      <!-- すべてのタスク -->
      <all-todo :todo-list="todoList" @deleteTodo="deleteTodo" />
    </div>
  </div>
</template>

<script>
import AddTodo from "./AddTodo.vue";
import CompletedTodo from "./CompletedTodo.vue";
import IncompleteTodo from "./IncompleteTodo.vue";
import AllTodo from "./AllTodo.vue";

export default {
  name: "Todo",
  components: {
    AddTodo,
    CompletedTodo,
    IncompleteTodo,
    AllTodo,
  },
  data() {
    return {
      todoList: [
        { title: "牛乳買ってくる", status: true },
        { title: "髪切る", status: true },
        { title: "ゴミを捨てる", status: true },
      ],
    };
  },
  updated() {
    console.log(this.inCompletedTodoList);
  },
  computed: {
    completedTodoList() {
      return this.todoList.filter((item) => item.status);
    },
    inCompletedTodoList() {
      return this.todoList.filter((item) => !item.status);
    },
  },
  methods: {
    addNewTodo(newTodo) {
      this.todoList.push({
        title: newTodo,
        status: false,
      });
    },
    deleteTodo(targetIndex) {
      this.todoList = this.todoList.filter((item, index) => {
        return index !== targetIndex;
      });
    },
    changeStatus(targetIndex) {
      this.todoList.forEach((item, index) => {
        if (index === targetIndex) {
          item.status = !item.status;
        }
      });
    },
  },
};
</script>

<style lang="scss">
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
  min-width: 250px;
  padding: 10px;
  background-color: #fff;
}

.card + .card {
  margin-top: 20px;
}

.contents-wrapper {
  margin-top: 12px;
  text-align: left;
  padding-left: 20px;
}

.contents-wrapper input + span {
  margin-left: 5px;
}
</style>
