<template>
  <div>
    <h1>{{ title }}</h1>
    <Button 
    @btn-click="$emit('toggle-add-task')"
    :text="showAddTask ? 'Add Task' : 'Close' " 
    :color="showAddTask ? 'Red' : 'Green' "></Button>
  </div>
</template>

<script>
import Button from "./Button";
export default {
  name: "Header",
  props: {
    title: {
      type: String,
    },
    showAddTask: {
        type: Boolean,
    }
  },
  components: {
    Button,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
