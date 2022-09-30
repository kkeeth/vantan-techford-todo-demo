<template>
  <button @click="handleClick" :disabled="isDisabled">
    {{ title }}
  </button>
</template>

<script>
export default {
  name: "VButton",
  emits: ["click"],
  props: {
    title: {
      type: String,
      required: false,
      default: "削除",
    },
    isDisabled: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  methods: {
    handleClick() {
      this.$emit("click");
    },
  },
};
</script>

<style scoped>
button {
  color: #fff;
  background-color: #eb6100;
  padding: 4px 8px;
  border-radius: 8px;
  border: 1px solid #fff;
  margin-left: 5px;
}
button:hover {
  cursor: pointer;
}
button:disabled {
  background: #999;
}
button:not(:disabled):hover {
  opacity: 0.7;
  transition: 0.3s;
  box-shadow: 0px 2px 3px 0px rgba(0, 0, 0, 0.3);
}
</style>
