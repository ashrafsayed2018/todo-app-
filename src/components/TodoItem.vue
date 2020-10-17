<template>
    <div class="todo-item" :class="{'is-complete' : todo.completed}">
        <p>
            <input type="checkbox"  :id="todo.id" @change="markeComplete">
             {{todo.title}} 

             <button class="del" @click="$emit('del-todo')">X</button>
        </p>
    </div>
</template>

<script>
export default {
    name : "TodoItem",
    props : ['todo'],
    methods : {
        markeComplete() {
            this.todo.completed = !this.todo.completed
        }
    }
}
</script>
<style scoped>
.todo-item {
    background-color: #f4f4f4;
    padding: .7rem;
    border-bottom: 1px dotted #ccc;
}
.is-complete {
    text-decoration: line-through;
}
.del {
    background-color : rgb(179, 14, 14);
    color: #fff;
    border:none;
    outline: none;
    padding: .3rem .7rem;
    float: right;
    border-radius: 50%;
    cursor: pointer;
}
</style>