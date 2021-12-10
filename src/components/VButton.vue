<template>
  <button @click="handleClick">{{ title }}</button>
</template>

<script>
export default {
  name: "VButton",
  props: {
    title: {
      type: String,
      required: true,
    },
  },
  methods: {
    handleClick() {
      this.$emit("click");
    },
  },
};
</script>

<style lang="scss" scoped>
button {
  color: #fff;
  background-color: #eb6100;
  padding: 4px 8px;
  border-radius: 8px;
  margin-left: 5px;
}

button:hover {
  background: #f56500;
}
</style>
