<template>
  <div id="app" style="text-align: center">
    <div style="display: inline-block">
      <h1 style="color: grey; opacity: 50%; left: 60px;"> To-Do List</h1>
      <AddTodo v-on:add-todo="addTodo"/>
      <Todos v-bind:todos="todos" v-on:delete-todo="deleteTodo"/>
    </div>
  </div>
</template>

<script>

import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";

import 'bootstrap'
import 'bootstrap/dist/css/bootstrap.min.css'

/*
The application consists mainly of two components: A todolist and todoitems, where the
todolist consists of none or multiple todoitems.

The todolist is implemented in the Todos.vue component and the todoitems are implemented in
the Todo.vue component. They are stored in an array

There is one additional vue component, AddTodo.vue, which handles the action of adding new
tasks to the todolist, by generating a new todoitem.
 */

export default {
  name: 'app',
  components: {
    AddTodo,
    Todos
  },
  data(){
    return {
      todos: [
        {
          id: 1,
          title: 'Wake Up',
          completed: false
        },
        {
          id: 2,
          title: 'Make Coffee',
          completed: false
        },
        {
          id: 3,
          title: 'Write Code',
          completed: false
        },
        {
          id: 4,
          title: 'Make more Coffee',
          completed: false
        },

      ],
    }
  },
  methods: {

    addTodo(newTodoObject) {
      /*
      Adds new todoitem, which was created in the AddTodo.vue component to the array of todoitems.
      */
      this.todos = [...this.todos, newTodoObject];
    },

    deleteTodo(todoID){
      /*
      Deletes a todoitem from the array of todoitems. The act of deleting is handled in the Todos.vue component.
      */
      this.todos = this.todos.filter(todo => todo.id !== todoID);
    }
  }
}
</script>

<style>

</style>
