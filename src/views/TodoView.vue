<template>
  <div class="container">
    <h1>はじめてのTODOアプリ</h1>
    <div class="contents">
      <todo />
    </div>
  </div>
</template>

<script>
import Todo from "@/components/todos/Todo.vue";

export default {
  name: "TodoView",
  components: {
    Todo,
  },
};
</script>

<style>
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
</style>
