<template>
  <div id="app">
     <Header />
     <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" /> <!-- passing in the todos from the data -->
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';

export default {
  name: 'app',
  components: {
    Header,
    Todos
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Todo One",
          completed: false
        },
        {
          id: 2,
          title: "Todo Two",
          completed: true
        },
        {
          id: 3,
          title: "Todo Three",
          completed: false
        },
      ]
    }
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id !== id); // filter is a high order array method; take current todos and filter and return an array based on condition so we only want everything that isnt deleted
    }
  }
}
</script>

<style>
 * {
   box-sizing: border-box;
   margin: 0;
   padding: 0;
 }

 body{
   font-family: Arial, Helvetica, sans-serif;
   line-height: 1.4;
 }
</style>
