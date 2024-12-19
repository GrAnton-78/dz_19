<template>
  <section class="real-app">
  <input
      type="text"
      class="add-input"
      autofocus="autofocus"
      placeholder="Введите задачу"
      v-on:keyup.enter="addTodo"
    />

    <Item
      v-for="todo in renderTodos"
      :todo="todo"
      :key="todo.id"
      v-on:del="deleteTodo"
    />
  </section>
</template>

<script>
import Item from "./item.vue";

let id = 0;

export default {
  data() {
   return {
     todos: [],
    };
  },
  components: {
   Item,
   },
  computed: {
    renderTodos() {
      return this.todos;
    },
  },
  methods: {
    addTodo(e) {
      this.todos.unshift({
        id: id++,
        content: e.target.value,
       });

      e.target.value = "";
      },
    deleteTodo(id) {
      this.todos.splice(
      this.todos.findIndex((todo) => id === todo.id),
        1
      );
    },
  },
};
</script>

<style scoped>
.real-app {
  padding: 20px;
  width: 600px;
  margin: 0 auto;
  box-shadow: 0 0 15px #05078b;
  background-color:  rgba(138, 166, 226, 0.3);
}
.add-input {
  background-color: rgba(138, 166, 226, 0.4);
  border-radius: 5px;
  border: none;
  font-size: 20px;
  border-bottom: 3px solid #141296;
  color: #05012b !important;
  padding: 20px;
  width: 400px;
}
</style>
