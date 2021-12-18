<template>
  <div class="home">
    <todo />
  </div>
</template>

<script>
// @ is an alias to /src
import Todo from "@/components/Todo.vue";

export default {
  name: "Home",
  components: {
    Todo,
  },
};
</script>

<style lang="scss" scoped></style>
