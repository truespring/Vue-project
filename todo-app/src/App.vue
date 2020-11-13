<template>
  <div id="app">
    <TodoHeader/>
    <TodoInput/>
  </div>
</template>

<script>
import TodoHeader from './components/todoHeader';
import TodoInput from './components/todoInput';

export default {
  name: 'App',
  components: {
    TodoHeader,
    TodoInput
  }
}
</script>

<style>

</style>
