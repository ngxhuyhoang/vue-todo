<template>
  <div class="todo-item">
    <p :class="isCompleted ? 'completed' : ''">
      <input type="checkbox" :checked="isCompleted" />
      {{ content }}
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["content", "isCompleted"],
};
</script>

<style scoped>
.todo-item {
  margin: 8px 16px;
  padding: 16px;
  background: #fff;
  border-radius: 5px;
  box-shadow: 5px 5px 5px #ccc;
}

.completed {
  text-decoration: line-through;
}
</style>