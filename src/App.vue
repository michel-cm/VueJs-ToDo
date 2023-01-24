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
        <div class="tile flex-centered" v-for="t in todos" :key="t.id">
          <div class="tile-icon">
            <i class="icon icon-time "></i>
          </div>
          <div class="tile-content">
            <div class="tile-subtitle">{{ t.description }}</div>
          </div>
          <div class="tile-action">
            <button class="btn btn-link">Concluído</button>
            <button class="btn btn-link">
              <span class="text-error">Remover</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
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
