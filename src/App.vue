<template>
  <div id="app">
    <div class="container">
      <h1 id="title">Todo-List App</h1>
      <div id="addItem">
        <input type="text" placeholder="item goes here..." v-model="newItem" @keypress.enter="addItem">
        <button @click="addItem" id="addButton">Add Item</button>
      </div>
      <TodoList :items="items" @delete-item="deleteItem" />
    </div>
  </div>
</template>

<script>
import TodoList from './components/TodoList'

export default {
  name: 'App',
  components: {
    TodoList
  },
  data() {
    return {
      items: [],
      newItem: ''
    }
  },
  methods: {
    addItem() {
      if (this.newItem === '') {
        alert('No item was put')
      } else {
        this.items.push(this.newItem)
        this.newItem = ''
      }  
    },
    deleteItem($event) {
      this.items.splice($event, 1)
    }
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 5px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

.container {
  background-color: rgb(86, 166, 190);
  color: white;
  margin: auto;
  width: 400px;
  min-height: 600px;
  padding: 10px;
  border-radius: 10px;
}

#addButton {
  border: none;
  background-color: rgb(255, 174, 0);
  color: white;
  border-radius: 3px;
  padding: 3px 5px;
}

input[type="text"] {
  border-radius: 25px;
  border: none;
  height: 20px;
}
</style>
