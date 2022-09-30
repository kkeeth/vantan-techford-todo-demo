<template>
  <todo-add-card @addTodo="addNewTodo" />
  <todo-list-card
    title="すべてのタスク"
    :todo-list="todoList"
    @deleteTodo="deleteTodo"
  />
  <todo-list-card
    title="完了済みタスク"
    :todo-list="completedTodoList"
    @deleteTodo="deleteTodo"
  />
  <todo-list-card
    title="未完了タスク"
    :todo-list="inCompletedTodoList"
    @deleteTodo="deleteTodo"
  />
</template>

<script>
import TodoAddCard from "./TodoAddCard.vue";
import TodoListCard from "./TodoListCard.vue";

export default {
  name: "ToDo",
  components: {
    TodoAddCard,
    TodoListCard,
  },
  props: {
    msg: String,
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

<style scoped>
.card + .card {
  margin-top: 20px;
}
</style>
