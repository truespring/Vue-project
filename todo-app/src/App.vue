<template>
  <div id="app">
    <TodoHeader/>
    <TodoInput @sendTodo="parentSendTodo" />
    <TodoList :todoList="todoList" @removeItem="parentDelTodo" />
    <TodoFooter @clearAllItem="parentClearAlltodo"/>
  </div>
</template>

<script>
import TodoHeader from './components/todoHeader';
import TodoInput from './components/todoInput';
import TodoList from './components/todoList';
import TodoFooter from './components/todoFooter';

export default {
  name: 'App',
  components: {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter,
  },
  data() {
    return {
      id: 0,
      todoList: []
    }
  },
  methods: {
    parentSendTodo(todo) {
      var obj = {
        id: this.id++,
        todo: todo
      }
      this.todoList.push(obj)
    },
    parentDelTodo(id) {
      var idx = this.todoList.findIndex(function(item) {
        return item.id == id;
      }); // 해당 인덱스를 찾는 방법
      this.todoList.splice(idx, 1);
    },
    parentClearAlltodo() {
      this.todoList = [];
    },
  }
}
</script>

<style>
body {
  text-align: center;
  background-color: #f6f6f6;
}
input {
  border-style: groove;
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
