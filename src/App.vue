<template>
  <!-- <h1>Hello World!</h1>
  <h2>{{ message }}</h2>
  <h1>Food</h1>
  <div id="wrapper">
    <food-item v-bind:is-favorite="true" food-name="Apples" food-desc="Apples are a type of fruit that grow on trees." />
    <food-item v-bind:is-favorite="false" food-name="Pizza"
      food-desc="Pizza has a bread base with tomato sauce, cheese, and toppings on top." />
    <food-item v-bind:is-favorite="false" food-name="Rice" food-desc="Rice is a type of grain that people like to eat." />
    <food-item v-bind:is-favorite="false" food-name="Paddy" />
  </div>
  <button @click="removeItem">Remove Item</button>
  <div id="parent">
    <food-item v-for="x in foods" v-bind:food-name="x" />
    <food-item v-for="x in foods" :key="x.name" :food-name="x.name" :food-desc="x.desc" :is-favorite="x.favorite"
      @toggle-favorite="receiveEmit" />
  </div> -->

  <!-- <h3>Todo List</h3>
  <p>In this example, the style attribute falls through from App.vue into the li element which is the components root
    element.</p>
  <ul>
    <todo-item v-for="x in items" :key="x" :item-name="x" style="background-color: lightgreen;" />
  </ul>
  <input placeholder="Add things to do here" v-model="newItem" @keydown.enter="addItem">
  <button @click="addItem">Add</button> -->

  <!-- <div>
    <h3>Global Styling</h3>
    <p>This p-tag belongs to 'App.vue'</p>
    <comp-one />
    <comp-two />
  </div> -->

  <!-- <div>
    <h3>Global Components</h3>
    <p>App.vue</p>
    <p>The CompOne.vue component is used inside both App.vue and CompTwo.vue.</p>
    <comp-one /> <br>
    <comp-two />
  </div> -->

  <!-- <div>
    <h3>Slots in Vue</h3>
    <p>We send 'Hello World!' as content to the slot tag inside the SlotComp.vue component from App.vue.</p>
    <slot-comp>Hello World!</slot-comp>
  </div> -->

  <!-- <h3>Slots in Vue</h3>
  <p>We create card-like div boxes from the foods array.</p>
  <div id="wrapper">
    <slot-comp v-for="x in foods">
      <img v-bind:src="x.url">
      <h4>{{ x.name }}</h4>
      <p>{{ x.desc }}</p>
    </slot-comp>
  </div> -->

  <!-- <h2>Re-usable Slot Cards</h2>
  <p>We create card-like div boxes from the foods array.</p>
  <p>We also create a card-like footer by reusing the same component.</p>
  <div id="wrapper">
    <slot-comp v-for="x in foods">
      <img v-bind:src="x.url">
      <h4>{{ x.name }}</h4>
    </slot-comp>
  </div>
  <footer>
    <slot-comp>
      <h3>Footer</h3>
    </slot-comp>
  </footer> -->

  <!-- <h3>Slots Fallback Content</h3>
  <p>A component without content provided can have fallback content in the slot tag.</p>
  <slot-comp>
    Empty
  </slot-comp>
  <slot-comp>
    <h4>This content is provided from App.vue</h4>
  </slot-comp> -->

  <h1>App.vue</h1>
  <p>The component has two div tags with one slot in each.</p>
  <slot-comp>'Hello!'</slot-comp>
</template>

<script>
import CompOne from './components/CompOne.vue';

export default {
  components: {
    'comp-one': CompOne
  },
  data() {
    return {
      message: 'This is some text',
      //foods: ['Apples', 'Pizza', 'Rice', 'Fish', 'Cake'],
      foods: [
        {
          name: 'Apples',
          desc: 'Apples are a type of fruit that grow on trees.',
          favorite: true,
          url: 'img_apple.svg'
        },
        {
          name: 'Pizza',
          desc: 'Pizza has a bread base with tomato sauce, cheese, and toppings on top.',
          favorite: false,
          url: 'img_pizza.svg'
        },
        {
          name: 'Rice',
          desc: 'Rice is a type of grain that people like to eat.',
          favorite: false,
          url: 'img_rice.svg'
        },
        {
          name: 'Fish',
          desc: 'Fish is an animal that lives in water.',
          favorite: true,
          url: 'img_fish.svg'
        },
        {
          name: 'Cake',
          desc: 'Cake is something sweet that tastes good.',
          favorite: false,
          url: 'img_cake.svg'
        }
      ],
      newItem: '',
      items: ['Buy apples', 'Make pizza', 'Mow the lawn']
    }
  },
  methods: {
    removeItem() {
      this.foods.splice(1, 1);
    },
    // receiveEmit() {
    //   alert('Hello World!');
    // }
    receiveEmit(foodId) {
      //alert('You clicked: ' + foodId);
      const foundFood = this.foods.find(
        food => food.name === foodId
      );
      foundFood.favorite = !foundFood.favorite;
    },
    addItem() {
      this.items.push(this.newItem);
      this.newItem = '';
    }
  }
}
</script>

<style>
#app {
  width: 300px;
}

#app>div {
  border: dashed black 1px;
  display: inline-block;
  margin: 10px;
  padding: 10px;
  background-color: lightgreen;
}

#app>div:hover {
  cursor: pointer;
}

#wrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

#wrapper img {
  display: block;
  margin: 20% auto 0;
  width: 60%;
}

#wrapper>div {
  border: dashed black 1px;
  flex-basis: 120px;
  margin: 10px;
  padding: 10px;
  background-color: lightgreen;
}

#parent {
  display: flex;
  flex-wrap: wrap;
}

#parent>div {
  border: dashed black 1px;
  margin: 10px;
  padding: 0 20px;
  background-color: lightgreen;
}

ul {
  width: 150px;
  list-style-type: none;
  padding-left: 10px;
}

p {
  width: 200px;
}

#app div {
  border: dashed black 1px;
  margin: 10px;
  padding: 10px;
  display: inline-block;
}

.compOneDiv {
  background-color: lightgreen;
}

.compTwoDiv {
  background-color: lightcoral;
}

footer>div {
  background-color: lightpink;
}

h3,
h4 {
  text-align: center;
}
</style>