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
      {{ todos }}
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
    },
  },
};
</script>

<style scoped>
.imgLogo {
  max-width: 80px;
  margin: 0 auto;
}
</style>
