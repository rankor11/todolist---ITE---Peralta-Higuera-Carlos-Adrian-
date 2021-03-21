<template>

  <div id="app" class="container">
      <h2>LKMX - Front End</h2>
      <h2>To Do List</h2>
      
      <TodoAdd v-on:add="addTodo"/>
      <TodoItem v-on:edit="editTodo"/>
      <Todo v-bind:todoslist="todos" v-on:remove-todo="removeTodo"/>
      
  </div>
</template>

<script>
import Todo from './components/Todo.vue' 
import TodoAdd from './components/TodoAdd' 
import TodoItem from './components/TodoItem' 

import {uuid} from 'vue-uuid'

export default {
  name: 'App',
  components: {
    Todo, TodoAdd, TodoItem
  },
  data(){
    return {
      
      todos: [
        {
          id: uuid.v4(), 
          title: 'Tarea 1: Hacer el test',
          
        },
        {
          id: uuid.v4(), 
          title: 'Tarea 2: Prueba',
          
        },
        {
          id: uuid.v4(), 
          title: 'Tarea 3: Prueba 2',
          
        },
      ],
      
    }
  },
  methods:{
    addTodo(todo){
     if(todo.title.trim().length === 0 ){
       confirm('Por favor escribe una tarea')
       return
     }
      this.todos.push(todo);
    },
  /*  editTodo(todo){
      console.log('prueba');
    },*/
    removeTodo(id){
     // this.todos.splice(id,1); <- no funciona debido a los id, 
     //filter para "eliminar" de acuerdo al valor del elemento
     this.todos = this.todos.filter(todo => todo.id != id)
    },
    
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

body{
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1.3em;
  background-color: #E6E8E8 ;
}

.container{
  border-radius: 20px;
  max-width: 600px;
  margin: 50px auto;
  padding-bottom: 10px;
  background-color: white;
  box-shadow: 0 12px 16px 0 rgba(0, 0, 0, 0.30);
}

h2{
  padding: 5px 10px;
  margin: 0;
}
</style>
