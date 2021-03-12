<template>
  <section id="app">
    <button @click.right="printEvent('some value', $event)">Click event</button>
    <br>
    <a href @click.prevent="onLinkClick" >Link</a>
    <br>

    <input type="text" @keyup.enter="onKeyUp">
    <h1>{{text}}</h1>
  </section>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  // components: {HelloWorld}
  data: () => ({
    text: '',
  }),
  methods: {
    printEvent(value, e) {
      console.log(value, e);
    },
    onLinkClick(){
      console.log('link click')
    },
    onKeyUp(e){
      console.log(e);
      this.text = e.target.value;
    }
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
