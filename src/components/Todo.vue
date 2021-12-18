<template>
  <div class="container">
    <h1>はじめてのTODOアプリ</h1>

    <div class="contents">
      <!-- タスクを追加のカード -->
      <add-todo @addTodo="addNewTodo" />

      <!-- 完了済タスク -->
      <completed-todo :todo-list="completedTodoList" @deleteTodo="deleteTodo" />

      <!-- 未完了タスク -->
      <incomplete-todo
        :todo-list="inCompletedTodoList"
        @deleteTodo="deleteTodo"
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
        { title: "牛乳買ってくる", status: false },
        { title: "髪切る", status: false },
        { title: "ゴミを捨てる", status: false },
      ],
    };
  },
  computed: {
    completedTodoList() {
      return this.todoList.filter((item) => item.status);
    },
    inCompletedTodoList() {
      return this.todoList.filter((item) => !item.status);
    },
  },
  beforeMount() {
    // 画面がレンダリングする前に実行
    this.reStoreItem();
  },
  updated() {
    this.storeItem();
  },
  methods: {
    addNewTodo(newTodo) {
      // 同じ名前のタスクがないか確認
      const duplicatedCheck = this.todoList.some((item) => {
        return item.title === newTodo;
      });

      if (duplicatedCheck) {
        alert("同じ名前のタスクが存在します．");
        return;
      } else {
        this.todoList.push({
          title: newTodo,
          status: false,
        });
      }
    },
    deleteTodo(targetIndex) {
      this.todoList = this.todoList.filter((_item, index) => {
        return index !== targetIndex;
      });
    },
    storeItem() {
      // ローカルストレージにデータを保存
      localStorage.setItem("todo-list", JSON.stringify(this.todoList));
    },
    reStoreItem() {
      // ローカルストレージからデータを復元
      if (JSON.parse(localStorage.getItem("todo-list"))) {
        this.todoList = JSON.parse(localStorage.getItem("todo-list"));
      }
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
  box-shadow: 0px 4px 5px 0px rgba(0, 0, 0, 0.3);
}

.card + .card {
  margin-top: 20px;
}

.contents-wrapper {
  margin-top: 12px;
  text-align: left;
  padding-left: 20px;
}

.contents-wrapper li {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

li + li {
  margin-top: 10px;
}

.contents-wrapper li span.disabled {
  color: #999;
  text-decoration: line-through;
}

.contents-wrapper input + span {
  margin-left: 5px;
}
</style>
