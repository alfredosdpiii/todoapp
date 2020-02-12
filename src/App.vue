<template>
  <div id="app">
   <p>App</p>
   <Todo v-bind:todos="todos" v-on:del-todo="deleteTodo"></Todo>
   <AddTodo v-on:addTodo="addTodo"></AddTodo>
  </div>
</template>

<script>
import Todo from './components/Todo'
import AddTodo from './components/AddTodo'

export default {
  name: 'App',
  components: {
    Todo,
    AddTodo
  },
  data() {
    return {
     todos: [
       {
         id:1,
         title:'do this',
         isDone:false,
         isEditing:false
       },
       {
         id:2,
         title:'do this later',
         isDone:false,
         isEditing:false
       },
       {
         id:3,
         title:'do this tomorrow',
         isDone:false,
         isEditing:false
       }
     ]
    }
  },
    methods:{
        addTodo(newTodo) {
          this.todos = [...this.todos, newTodo];
          
       
        },
        deleteTodo(id){
           this.todos = this.todos.filter(todo => todo.id !== id)
        
        }
  }
  
}
</script>

<style>

</style>
