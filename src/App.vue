<template>
  <div class="center">
    <TodoList></TodoList>
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";

export default {
  components: {
    TodoList
  }
}
</script>

<style>
.center {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
