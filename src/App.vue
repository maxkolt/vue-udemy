<template>
  <section id="app">
    <h1>{{ firstName }}</h1>
    <h2>{{ num * 3 }}</h2>
    <h3>{{ obj }}</h3>
    <a v-bind:href="linkUrl">Link</a>

  </section>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  // components: {HelloWorld}
  data: () => ({
    firstName: 'Max',
    num: 10,
    obj: {
      age: 30
    },
    linkUrl: 'http//google.com'
  }),
  methods:{
  }

}

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
