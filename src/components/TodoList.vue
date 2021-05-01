<template>
  <div>
    <h1>{{ msg }}</h1>

    <div id="todo-list">
      <ul v-for="todo in todos" :key="todo.id">
        <li>{{ todo.text }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: { todos: Array, msg: String },
  methods: {
    getTodos() {
      return localStorage.getItem("HelloWorld");
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

a {
  color: #42b983;
}
</style>
