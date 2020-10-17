<template>
    <div id="todos">
         <ul>
             <li v-for="todo in todos" :key="todo.id">
             <TodoItem v-bind:todo="todo" @del-todo="$emit('del-todo',todo.id)"/>
             </li>
         </ul>
         
    </div>
</template>
<script>
import TodoItem from "./TodoItem"
export default {
    name : "Todos",
    components : {
        TodoItem
    },
    data () {
          return {

          }
    },
    props : ['todos']
}
</script>

<style scoped>

</style>