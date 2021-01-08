<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <h1>Firstname : {{ firstname }}</h1>
    <h1>Alt Name : {{ altName }}</h1>
    <button @click="mydetails">Click me!</button>
    <button @click="$emit('msg-from-child', 'Hi, dad')">Emit to parent</button>
    <h1 v-if="clicked">{{ fullname }}</h1>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data: function () {
    return {
      firstname: "Mahadevan",
      altName: "Allen",
      clicked: false,
    };
  },
  methods: {
    mydetails: function () {
      this.clicked = !this.clicked;
      return "I am " + this.firstname + " aka " + this.altName;
    },
  },
  computed: {
    fullname: function () {
      return this.firstname + " - Computed - " + this.altName;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
