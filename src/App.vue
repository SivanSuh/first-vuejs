<template>
  <div id="app">
    <Navbar />
    <form @submit.prevent="addButton">
      <input type="text" id="todo" v-model="newItem" />
      <button type="submit" class="btn">Add</button>
      <ul v-for="items in item" v-bind:key="items.id">
        <li>{{ items.text }}</li>
        <button class="delete" v-on:click="deleteButton(items.id)">
          Delete
        </button>
      </ul>
    </form>
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
export default {
  components: { Navbar },
  name: "App",
  data() {
    return {
      newItem: "",
      item: [],
    };
  },
  methods: {
    addButton() {
      if (this.newItem.length === 0) {
        return;
      } else {
        this.item.push({ id: Math.random(), text: this.newItem });
        this.newItem = "";
      }
    },
    deleteButton(todoId) {
      this.item = this.item.filter((todo) => todo.id != todoId);
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
ul {
  list-style-type: none;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: yellow;
  margin: 15px;
}

input {
  outline: none;
  padding: 5px;
}
li {
  padding: 5px;
  margin: 5px 10px;
}
.btn {
  padding: 5px;
  background-color: gray;
  color: white;
  border: none;
  margin-left: 3px;
}
.btn:hover {
  color: red;
}
.delete {
  background-color: red;
  color: white;
  border: none;
  padding: 5px;
}
.delete:hover {
  color: purple;
}
form {
  margin: 30px 10px;
}
</style>
