<template>
  <button
    :style="{ backgroundColor: backgroundColor, color: color }"
    @click="onClick()"
  >
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: {
      type: String,
      default: "Add task",
    },
    backgroundColor: {
      type: String,
      default: "lightblue",
    },
    color: {
      type: String,
      default: "white",
    },
  },
  methods: {
    onClick() {
      this.$emit('toggle-add-task');
    },
  },
};
</script>

<style scoped>
button {
  outline: none;
  border: none;
  padding: 5px;
  border-radius: 5px;
}
</style>