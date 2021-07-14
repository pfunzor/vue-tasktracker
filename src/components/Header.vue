<template>
  <header>
    <h1>{{ heading }}</h1>
    <Button
      @click="$emit('show-add-task')"
      :text="isOpen ? 'Cancel' : 'Add Task'"
      :color="isOpen ? 'Red' : 'green'"
    ></Button>
  </header>
</template>

<script>
import Button from "./Button.vue";
export default {
  name: "Header",
  props: {
    heading: String,
    isOpen: Boolean,
  },

  components: {
    Button,
  },
  emits: ["show-add-task"],
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}
</style>
