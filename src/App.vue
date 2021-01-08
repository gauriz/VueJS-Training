<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld
      msg="Welcome to Your Vue.js App"
      v-on:msg-from-child="fromChild($event)"
    />
    <p v-if="msg != ''">Message from Child = {{ msg }}</p>
    <hr />

    <!-- Multiple Instances of a component -->
    <HelloWorld
      v-for="post in posts"
      v-bind:key="post.id"
      v-bind:msg="post.title"
    /> 
     <hr />

    <!-- MODEL -->
    <!-- <input v-model="modelText" />

    {{ modelText }} <br />
    <button @click="changeModel">Click me to change the model value!</button> -->

    <LifeCycleHooks />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import LifeCycleHooks from "./components/LcHooks.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    LifeCycleHooks,
  },
  data: function () {
    return {
      msg: "",
      modelText: "",
      posts: [
        { id: 1, title: "My journey with Vue" },
        { id: 2, title: "Blogging with Vue" },
        { id: 3, title: "Why Vue is so fun" },
      ],
    };
  },
  methods: {
    fromChild: function (msg) {
      this.msg = msg;
    },
    changeModel: function () {
      this.modelText = "New Model Value";
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
