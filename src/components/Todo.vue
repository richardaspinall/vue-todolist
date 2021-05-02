<template>
  <div class="todo">
    {{ todoObj.text }}
    <button v-on:click="deleteTodo()">Delete</button>
  </div>
</template>

<script>
export default {
  name: "Todo",
  props: { todo: Object, todos: Array },
  data() {
    return {
      todoObj: this.todo,
    };
  },
  methods: {
    deleteTodo() {
      const indexOfTodoToDelete = this.todos.findIndex(
        (todoInArray) => todoInArray.id === this.todoObj.id
      );
      this.todos.splice(indexOfTodoToDelete, 1);
      const unparsedTodos = {
        todos: this.todos,
      };
      const parsedTodos = JSON.stringify(unparsedTodos.todos);
      localStorage.setItem("todos", parsedTodos);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
