<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import TestComponent from "@/components/TestComponent.vue";

export default {
  name: "Home",
  components: {
    HelloWorld,
    TestComponent,
  },
};
</script>
<template>
  <div class="test">
    <h1>This is a test page</h1>
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <TestComponent/>

  </div>
</template>