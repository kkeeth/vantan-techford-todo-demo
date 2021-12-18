<template>
  <div class="card">
    <div class="title">タスクを追加</div>
    <div class="contents-wrapper">
      <input v-model="inputTodo" type="text" placeholder="テキストを入力" />
      <v-button title="追加" @click="addTodo" :is-disabled="inputTodo.length === 0" />
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
  data() {
    return {
      inputTodo: "",
    };
  },
  methods: {
    addTodo() {
      this.$emit("addTodo", this.inputTodo);
      this.inputTodo = "";
    },
  },
};
</script>

<style scoped>
.contents-wrapper input {
  border: 1px solid #999;
  border-radius: 4px;
  padding: 2px 6px;
}
</style>
