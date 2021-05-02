<template>
  <div id="app">
    <TodoList :todos="todos" msg="TodoList" />
  </div>
</template>

<script>
// @ is an alias to /src
import TodoList from "@/components/TodoList.vue";

export default {
  name: "Home",
  metaInfo() {
    return {
      meta: [
        { name: "viewport", content: "width=device-width, initial-scale=1.0" },
      ],
    };
  },
  components: {
    TodoList,
  },
  data: function () {
    return {
      todos: [],
    };
  },
  mounted() {
    this.todos = JSON.parse(localStorage.getItem("todos"));
    if (!this.todos) {
      localStorage.setItem("todos", "[]");
    }
  },
};
</script>

<style lang="scss">
body {
  background-color: #748f83;
}
#app {
  font-family: lato, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 0 auto 0 auto;
  text-align: center;
  color: #2c3e50;
}
</style>
