<template>
  <div>
    <h1>{{ msg }}</h1>

    <div id="todo-list">
      <div>
        <input v-model="todoText" v-on:keyup.enter="addTodo()" />
        <button v-on:click="addTodo()">Add</button>
        <ul v-for="todo in todos" :key="todo.id">
          <li>
            <Todo :todo="todo" :todos="todos" />
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "@/components/Todo.vue";
export default {
  name: "TodoList",
  components: {
    Todo,
  },
  props: { todos: Array, msg: String },
  data() {
    return {
      todoText: "",
    };
  },
  methods: {
    addTodo() {
      if (/\S/.test(this.todoText)) {
        this.todos.push({ id: this.todos.length, text: this.todoText });
        const unparsedTodos = {
          todos: this.todos,
        };
        const parsedTodos = JSON.stringify(unparsedTodos.todos);
        localStorage.setItem("todos", parsedTodos);
        this.todoText = "";
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
</style>
