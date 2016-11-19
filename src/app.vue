<template>
  <div id="app">
    <hello></hello>
    <TodoList></TodoList>
  </div>
</template>

<script>
import Hello from './components/hello';
import TodoList from './components/todolist';

export default {
  components: {
    Hello,
    TodoList
  }
};
</script>
