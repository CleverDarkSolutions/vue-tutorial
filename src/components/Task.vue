<template>
  <div @dblclick="$emit('toggle-reminder', task.id)" 
  :class="[task.reminder ? 'reminder' : '', 'task']">
      <i @click="$emit('delete-task', id);" class="fas fa-times"></i>
    <h3>
        {{ task.text }}
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {
     
  }
};
</script>

<style scope>
.task {
    background : #f4f4f4;
    margin : 5px;
    padding: 10px 10px;
    cursor: pointer;
    line-height: 10px;
}

.task.reminder{
    border-left: 5px solid green;
}

.fas {
    color: red;
    position: relative;
    left: 220px;
}

</style>
