<template>
  <section id="app">

    <!--    <ul>-->
    <!-- <li v-for="(color, index) in colors" :key="index">Это индекс: {{ index }} это цвет: {{ color }}</li>-->
    <!-- <li v-for="user in users" :key="user.id">{{ user.name }} {{ user.age }}</li>-->
    <!--<li v-for="(value, name, index) in product" :key="value">{{ index }} {{ name }} {{ value }}</li>-->

    <!--<strong>{{ allUsersTotalAge }}</strong>-->
    <div>
      <!-- <input type="text" @keyup.enter="addNewColor"> -->
      <!--<input type="text" @keyup.enter="deleteProp">-->
      <section>
        <!--<button type="submit" @click="reverseString">Перевернуть</button>-->
        <!--<h2>{{ title }}</h2>-->
        <!--<button type="submit" @click="worldLength">Самое длинное</button>-->
        <!--<br>-->
        <!--<p>Самое длинное: {{ wordMax }}</p>-->
        <!--<br>-->
        <h1 class="title"
            :class="[classObj, activeClass]"
        >Hello World</h1>
      </section>
      <HelloWorld :user="user" :title="title" @onChangeCounter="onChengCounterInComponent"/>
      <br/>

      <input type="text" v-model="text">
      <h3>
        Input text value:
        <i>{{ text }}</i>
      </h3>
      <div class="checkboxes">
        <input type="checkbox" v-model="checkbox">
        <h3>
          Checkbox value:
          <i>{{ checkbox }}</i>
        </h3>
        <input type="checkbox" v-model="checkboxArray" value="one">
        <input type="checkbox" v-model="checkboxArray" value="two">
        <input type="checkbox" v-model="checkboxArray" value="three">
        <h3>
          CheckboxArr value:
          <i>{{ checkboxArray }}</i>
        </h3>
      </div>
      <select v-model="select">
        <option value="bmw">BMW</option>
        <option value="audi">Audi</option>
      </select>
      <h3>
        Select value:
        <i>{{ select }}</i>
      </h3>

    </div>
    <!--</ul>-->

  </section>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {HelloWorld},
  data: () => ({
    computed: {
      textComputed: {
        get(){
          return this.text;
        },
        set(value){
          console.log(value)
          this.text = value;
        }
      },
    },
    text: '',
    checkbox: false,
    checkboxArray: [],
    select: '',
    title: 'Some title',
    user: {
      name: 'Maxim'
    },

    colors: ['red', 'blue', 'black'],
    users: [
      {name: 'maksim', age: 28, id: '1'},
      {name: 'ivan', age: 34, id: '2'}
    ],
    product: {
      brand: 'Apple',
      model: 'Iphone 11',
      price: '$1000'
    },
    //title: 'Переверни меня И найди самое длинное',
    wordMax: '',
    activeClass: "inner-class",
    isActive: false
  }),
  computed: {
    allUsersTotalAge() {
      let total = 0;
      for (let user of this.users) {
        let age = user.age;
        total += age;
      }
      return total
    },
    classObj() {
      return {
        'active-class': this.isActive,
        "error": !this.isActive
      }
    }
  },
  methods: {
    onChengCounterInComponent(value) {
      console.log('In app vue, counter:', value);
    },

    worldLength() {
      let wordArray = this.title.split(' ');
      for (let w of wordArray) {
        if (w.length > this.wordMax.length) {
          this.wordMax = w;
        }
      }
    },
    addNewColor(e) {
      this.colors.push(e.target.value);
      this.colors[this.colors.length] = e.target.value;
    },
    deleteProp(e) {
      delete this.product[e.target.value];
      this.$delete(this.product, e.target.value);
    },
    reverseString() {
      this.title = this.title.split("").reverse().join("");
    },

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
}
</style>
