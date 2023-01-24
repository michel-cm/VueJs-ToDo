<template>
  <div id="app">
    <div class="container grid-xs py-2">
      <img
        class="img-responsive imgLogo"
        src="@/assets/logo.png"
        alt="logomarca"
      />
      <form @submit.prevent="addTodo(todo)">
        <div class="input-group">
          <input
            type="text"
            v-model="todo.description"
            class="form-input"
            placeholder="Novo todo"
          />
          <button class="btn btn-primary input-group-btn">Adicionar</button>
        </div>
      </form>

      <div class="todoList">
        <TodoItem v-for="t in todos" :key="t.id" :todo="t" />
      </div>
    </div>
  </div>
</template>

<script>
import TodoItem from "./components/TodoItem";

export default {
  name: "App",
  components: { TodoItem },
  data() {
    return {
      todos: [],
      todo: { checked: false },
    };
  },
  methods: {
    addTodo(todo) {
      todo.id = Date.now();
      this.todos.push(todo);
      this.todo = { checked: false };
    },
  },
};
</script>

<style scoped>
.imgLogo {
  max-width: 80px;
  margin: 0 auto;
}

.todoList {
  padding-top: 2rem;
}
</style>
