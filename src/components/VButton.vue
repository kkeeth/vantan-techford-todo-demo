<template>
  <button>{{ title }}</button>
</template>

<script>
export default {
  name: 'VButton',
  props: {
    title: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
button {
  color: #fff;
  background-color: #eb6100;
  padding: 4px;
  border-radius: 8px;

  /* &:hover {
    background: #f56500;
  } */
}

button:hover {
  background: #f56500;
}
</style>