<template>
  <div id="app">
   <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" @del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from "../components/Todos";
import AddTodo from "../components/addTodo";
// eslint-disable-next-line no-unused-vars
import axios from "axios";
export default {
  name : "Home",
  components : {
    Todos,
    AddTodo
  },
  data () {

       return {
          todos : []
       }
  },
    methods : {
        deleteTodo (id) {
          axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
          .then(()=> {
           this.todos =  this.todos.filter(todo =>  todo.id != id)
          })
          .catch(err => console.log(err))
       
        },
        addTodo(newTodo) {
          const {title,completed} = newTodo;
          axios.post('https://jsonplaceholder.typicode.com/todos',{
            title,
            completed
          })
          .then(res => {
             this.todos = [...this.todos,res.data]
            console.log('data was posted', res)
          })
          .catch(err => {
            console.log(err)
          })
          
        }
    },
    created () {
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(response => this.todos = response.data)
      .catch(err => {
        console.log(err)
      }) 
    }
}
</script>

<style>

*,*::after,*::before {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.btn {
  display: inline-block;
  border: none;
  outline: none;
  background-color: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background-color: #666;
}
</style>
