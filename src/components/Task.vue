<template>
  <div
    @dblclick="$emit('toogle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h3>
      {{ task.text }}
      <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
    </h3>
    <h5>{{ task.day }}</h5>
  </div>
</template>

<script>
export default {
  name: "task",
  props: {
    task: Object,
  },
  emits: ["delete-task", "toogle-reminder"],
};
</script>
<style scope>
.fas {
  color: rgb(156, 18, 18);
}

.fas:hover {
  font-size: 1.5em;
}

.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task:hover {
  background: #f4f4f46b;
  color: rgb(48, 76, 77);
  margin-left: 20px;
}

.task.reminder {
  border-left: 5px solid green;
}

.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
