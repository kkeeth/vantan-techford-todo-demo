<template>
  <div class="card">
    <div class="title">タスクを追加</div>
    <div class="contents-wrapper">
      <input type="text" placeholder="タスクを追加">
      <v-button title="追加" />
    </div>
  </div>
</template>

<script>
import VButton from './VButton.vue'

export default {
  name: 'CompletedTodo',
  components: {
    VButton
  }
}
</script>
