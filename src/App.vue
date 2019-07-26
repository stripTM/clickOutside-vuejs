<template>
  <div id="app">
    <OverlapComponent v-bind:options="options" v-if="ver"/>
    <button v-on:click="ver = !ver">off</button>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import OverlapComponent from './components/OverlapComponent.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    OverlapComponent
  },
  data() {
    return {
      ver: true,
      options: [
        {
          id: 0,
          label: 'Cero'
        },
        {
          id: 1,
          label: 'Uno'
        },
        {
          id: 2,
          label: 'Dos'
        },
      ]
    }
  },
  methods: {
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.selector {
  background-color: palegreen;
  cursor: pointer;
  width: 5em;
  text-align: left
}
.selector .current {
  text-align: center;
  display: block;
}
.selector .desplegado {
  background-color: aquamarine;
  margin: 0;
  padding: 0 0 0 1.5rem;
}
</style>
