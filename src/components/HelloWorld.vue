<template>
  <div>
    <h1>{{ message }}</h1>

    <div id="example-1">
      <button v-on:click="counter += 1">Add 1</button>
      <p>The button above has been clicked {{ counter }} times.</p>
      <button v-on:click="saveSomething()">Save something</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      message: this.msg,
      counter: 0,
    };
  },
  methods: {
    getSomething() {
      // Not good to do. Avoid updating the prop directly
      this.message = localStorage.getItem("HelloWorld");
    },
    saveSomething() {
      localStorage.setItem("HelloWorld", "Hello World");
      this.getSomething();
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
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
