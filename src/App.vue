<template>
  <section id="app">
    <ul>
      <!-- <li v-for="(color, index) in colors" :key="index">Это индекс: {{ index }} это цвет: {{ color }}</li>-->
      <!-- <li v-for="user in users" :key="user.id">{{ user.name }} {{ user.age }}</li>-->
      <li v-for="(value, name, index) in product" :key="value">{{ index }} {{ name }} {{ value }}</li>

      <strong>{{ allUsersTotalAge }}</strong>
      <div>
        <!-- <input type="text" @keyup.enter="addNewColor"> -->
        <input type="text" @keyup.enter="deleteProp">
      </div>
    </ul>

  </section>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  // components: {HelloWorld}
  data: () => ({
    colors: ['red', 'blue', 'black'],
    users: [
      {name: 'maksim', age: 28, id: '1'},
      {name: 'ivan', age: 34, id: '2'}
    ],
    product: {
      brand: 'Apple',
      model: 'Iphone 11',
      price: '$1000'
    }
  }),
  computed: {
    allUsersTotalAge() {
      let total = 0;
      for (let i = 0; i < this.users; i++) {
        let age = this.users[i].age;
        total += age;
      }
      return total;
    }
  },
  methods: {
    addNewColor(e) {
      this.colors.push(e.target.value);
      this.colors[this.colors.length] = e.target.value;
    },
    deleteProp(e) {
      //delete this.product[e.target.value];
      this.$delete(this.product, e.target.value);
    }
  },
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
