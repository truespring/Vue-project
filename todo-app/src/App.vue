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

  created() {
    this.selTodoList();
  },

  data() {
    return {
      id: 0,
      todoList: []
    }
  },

  methods: {
    selTodoList() {
      this.$http.get('/api/selTodoList').then((res) => {
        // console.log(res.data);
        this.todoList = res.data;
      })
    },

    parentSendTodo(todo) {
      let obj = {
        todo: todo
      }
      this.$http.post('/api/insTodo', obj).then((res) => {
        // console.log(res.data);
        this.selTodoList();
      })
    },

    parentDelTodo(i_todo) {
      // var idx = this.todoList.findIndex(function(item) {
      //   return item.i_todo == id;
      // }); // 해당 인덱스를 찾는 방법
      // this.todoList.splice(idx, 1);
      if(!confirm('정말 지우시겠습니까?')) {
        return false;
      }
      this.$http.delete('/api/delTodo', {
        params: {
          i_todo: i_todo
        }
      }).then((res) => {
        this.selTodoList();
      })
    },

    parentClearAlltodo() {
      if(!confirm('정말 다 지우시겠습니까?')) {
        return false;
      }
      this.$http.delete('/api/delTodo').then((res) => {
        this.selTodoList();
      })
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
