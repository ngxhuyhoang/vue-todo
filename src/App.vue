<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <h1>Todo App</h1>
  <div style="add-todo">
    <input placeholder="Type here..." type="text" v-model="newTask" />
    <button @click="addTodo(newTask)">Thêm</button>
  </div>
  <TodoItem
    v-for="(todo, index) in todos"
    :key="index"
    :content="todo.content"
    :isCompleted="todo.isCompleted"
    @click="markAsCompleted(index)"
  />
  <h3 v-show="!todos.length">Hôm nay chưa có việc gì làm</h3>
</template>

<script>
import TodoItem from "./components/TodoItem.vue";

export default {
  name: "App",
  components: {
    TodoItem,
  },
  data() {
    return {
      newTask: "",
      todos: [],
      isShowTodoList: false,
    };
  },
  methods: {
    markAsCompleted(index) {
      this.todos[index].isCompleted = !this.todos[index].isCompleted;
    },
    addTodo(content) {
      this.todos.unshift({ content, isCompleted: false });
      this.newTask = "";
    },
  },
};
</script>

<style scoped>
button {
  padding: 8px;
  cursor: pointer;
  background: green;
  color: #fff;
  border-radius: 5px;
  outline: none;
}

input {
  margin: 0px 16px;
  padding: 8px 16px;
  outline-color: green;
  border-radius: 5px;
}

.add-todo {
  display: flex;
  flex-direction: row;
}
</style>
