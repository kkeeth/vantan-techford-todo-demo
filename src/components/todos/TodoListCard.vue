<template>
  <div class="card">
    <div class="title">{{ title }}</div>
    <div class="contents-wrapper">
      <ul class="todo-list">
        <li v-for="(item, index) in todoList" :key="item.title">
          <label :for="item.title">
            <input type="checkbox" v-model="item.status" :id="item.title" />
            <span :class="item.status && 'disabled'">{{ item.title }}</span>
          </label>
          <v-button title="削除" @click="handleDelete(index)" />
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import VButton from "./VButton.vue";
export default {
  name: "TodoListCard",
  emits: ["deleteTodo"],
  components: {
    VButton,
  },
  props: {
    title: {
      type: String,
      required: true,
    },
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

<style>
.card {
  border: 1px solid #999;
  border-radius: 4px;
  min-width: 250px;
  padding: 10px;
  background-color: #fff;
  box-shadow: 0px 4px 5px 0px rgba(0, 0, 0, 0.3);
}
.card .title {
  margin-bottom: 1rem;
}
.contents-wrapper {
  margin-top: 12px;
  text-align: left;
}
.contents-wrapper ul {
  padding: 0 20px;
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
