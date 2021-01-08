<template>
  <div class="hello">hayyy - {{ counter }}</div>
</template>

<script>
export default {
  name: "LifeCycleHooks",
  data: function () {
    return {
      name: "Gauri",
      counter: 0,
      interval: null,
    };
  },
  beforeCreate: function () {
    // `this` points to the vm instance
    console.log("beforeCreate, a is: " + this.name);
  },
  created: function () {
    console.log("created, a is: " + this.name);
    this.interval = setInterval(() => {
      this.counter++;
    }, 2000);
    setTimeout(() => {
      clearInterval(this.interval);
    }, 1000 * 10);
  },
  beforeMount: function () {
    console.log(
      `beforeMount, At this point, vm.$el has not been created yet.`,
      this.$el
    );
  },
  mounted() {
    console.log(
      `mounted, At this point, vm.$el has been created and el has been replaced.`,
      this.$el.textContent
    );
  },
  beforeUpdate() {
    console.log(`beforeUpdate : `, this.counter);
  },
  updated() {
    console.log(`updated : `, this.counter);
  },
  beforeDestroy() {
    console.log(
      `At this point, watchers, child components, and event listeners have not been teared down yet.`
    );
    this.interval = null;
    delete this.interval; //unsubscribe things etc
  },
  destroyed() {
    console.log(
      `At this point, watchers, child components, and event listeners have been torn down.`
    );
    console.log(this);
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
