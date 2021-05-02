<template>
  <div id="app">
    <TodoList :todos="todos" msg="Todo List" />
  </div>
</template>

<script>
// @ is an alias to /src
import TodoList from "@/components/TodoList.vue";

export default {
  name: "Home",
  components: {
    TodoList,
  },
  data: function () {
    return {
      msg: "Hi there",
      todos: [],
    };
  },
  mounted() {
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
  width: 500px;
  margin: 0 auto 0 auto;
  text-align: center;
  color: #2c3e50;
  background-color: #748f83;
}
</style>
