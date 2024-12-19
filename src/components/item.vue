<template>
  <div class="todo-item">
    <div>{{ todo.content }}</div>
    <button @click="deleteTodo">Удалить</button>
  </div>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
    },
  },
  methods: {
       deleteTodo() {
       this.$emit("del", this.todo.id);
   },
  },
 };
</script>

<style scoped>
.todo-item {
  display: flex;
  justify-content: space-between;
  margin: 20px 0;
}
.todo-item {
  position: relative;
  font-size: 24px;
 border-bottom: 1px solid rgba(214, 21, 21, 0.06);
}
</style>
