<template>
  <div>
    <h1>Todo App</h1>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos"
          v-bind:todo="todo" :key="todo.title" />
  </div>
</template>

<script type = "text/javascript" >
import sweetalert from 'sweetalert';
import Todo from './Todo';

export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
      sweetalert('Deleted!', 'Your To-Do has been deleted.', 'success');
    },
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
      sweetalert('Success!', 'To-Do completed!', 'success');
    },
  },
};
</script>
<style>
</style>
