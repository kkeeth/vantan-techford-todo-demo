<template>
  <div class="card">
    <div class="title">未完了タスク</div>
    <div class="contents-wrapper">
      <ul class="todo-list">
        <li v-for="(item, index) in todoList" :key="index">
          <input type="checkbox" value="" />
          <span>{{ item.title }}</span>
          <v-button title="削除" />
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import VButton from "./VButton.vue";

export default {
  name: "IncompleteTodo",
  components: {
    VButton,
  },
  props: {
    todoList: {
      type: Array,
      required: true,
    },
  },
};
</script>
