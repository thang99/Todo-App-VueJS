<template>
  <header>
    <h2>{{ title }}</h2>
    <Button
      @toggle-add-task="$emit('toggle-add-task')"
      :text="!toggleText ? 'Add task' : 'Close'"
      :backgroundColor="!toggleText ? 'green' : 'red'"
      color="white"
      class="btn"
    />
  </header>
</template>

<script>
import Button from "./Button.vue";
export default {
  components: { Button },
  name: "Header",
  props: {
    title: {
      type: String,
      default: "Header",
    },
    toggleText: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style scoped>
header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 50px;
}
</style>