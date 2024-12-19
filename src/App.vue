<script setup>
import { ref } from "vue";

const items = ref(["clean the room", "read a book", "workout"]);
const input = ref("");

const Add = () => {
  if (!input.value.length) return;
  items.value.push(input.value);
  input.value = "";
};
const Remove = (i) => {
  items.value.splice(i, 1);
};
</script>

<template>
  <div class="container">
    <input id="userInput" type="text" v-model="input" />
    <button @click="Add">add</button>
  </div>
  <ul>
    <li v-for="(item, index) in items">
      <h4 @click="Remove(index)">x</h4>
      {{ index }} {{ item }}
    </li>
  </ul>
</template>

<style scoped>
.container {
  display: flex;
  input {
    padding: 10px;
    outline: none;
    border: none;
    border-radius: 10px 0px 0px 10px;
  }
  button {
    padding: 10px;
    font-weight: bold;
    border: none;
    border-radius: 0px 10px 10px 0px;
    background-color: gray;
    color: white;
    &:hover {
      background-color: white;
      color: gray;
    }
  }
}
li {
  text-align: left;
  list-style: none;
  display: flex;
  align-items: center;
  gap: 10px;

  h4 {
    cursor: pointer;
    background-color: gray;
    border-radius: 5px;
    display: flex;
    height: 20px;
    width: 20px;
    justify-content: center;
    align-items: center;
    &:hover {
      background-color: white;
      color: gray;
    }
  }
}
</style>
