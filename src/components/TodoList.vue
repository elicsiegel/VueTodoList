<template>
  <div>
    <div class='ui centered card' id="card-header">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
          </div>
          <div class='field'>
            <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
          </div>
        </div>
      </div>
    </div>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" :todo="todo"></todo>
  </div>
</template>

<script type = "text/javascript" >

  import Todo from './Todo';
  export default {
    props: ["todos"],
    components: {
      Todo,
    },
    methods: {
      deleteTodo(todo) {
        const todoIndex = this.todos.indexOf(todo);
        this.todos.splice(todoIndex, 1);
      },
      completeTodo(todo) {
        const todoIndex = this.todos.indexOf(todo);
        this.todos[todoIndex].done = true;
      },
    },
  };
</script>
<style>
  #card-header {
    margin-top: 10px;
  }
</style>
