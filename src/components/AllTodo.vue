<template>
  <div class="card">
    <div class="title">全てのタスク</div>
    <div class="contents-wrapper">
      <ul class="todo-list">
        <li v-for="(item, index) in todoList" :key="index">
          <input type="checkbox" value="" />
          <span>{{ item.title }}</span>
          <v-button title="削除" @click="handleDelete(index)" />
        </li>
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
  props: {
    todoList: {
      type: Array,
      required: true,
    },
  },
  methods: {
    handleDelete(index) {
      this.$emit("deleteTodo", index);
    },
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
