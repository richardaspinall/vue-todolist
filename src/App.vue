<template>
  <div id="app">
    <HelloWorld :msg="msg" />
    <TodoList :todos="todos" msg="Todo List" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import TodoList from "@/components/TodoList.vue";

export default {
  name: "Home",
  components: {
    HelloWorld,
    TodoList,
  },
  data: function () {
    return {
      msg: "Hi there",
      todos: [],
    };
  },
  mounted() {
    this.msg = localStorage.getItem("HelloWorld");

    let unparsedTodos = {
      todos: [
        { id: 0, text: "Vegetables" },
        { id: 1, text: "Cheese" },
        { id: 2, text: "Whatever else humans are supposed to eat" },
      ],
    };
    const parsedTodos = JSON.stringify(unparsedTodos.todos);
    localStorage.setItem("todos", parsedTodos);

    this.todos = JSON.parse(localStorage.getItem("todos"));
  },
};
</script>

<style lang="scss">
body {
  background-color: #fff;
}
#app {
  font-family: lato, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
