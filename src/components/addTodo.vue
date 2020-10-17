<template>
    <div>
    <form @submit.prevent="addTodo">
       <input type="text" name="title" v-model="title" placeholder="add todo ...">
       <input type="submit" value="submit" class="btn">
    </form>
    </div>
</template>
<script>
export default {
    name : "AddTodo",
    data () {
        return {
            title : '',
             newTodo : {
                title : this.title,
                completed : true
            }
        }
    },
    methods : {
        addTodo() {
            const newTodo = {
                id :Math.ceil( Math.random() * 1000),
                title : this.title,
                completed : false
            }
            // send up to the parent
            this.$emit('add-todo',newTodo)
            this.title = ''
        }
    }
}
</script>
<style scoped>
form {
    display: flex;
}
input[type="text"] {
    flex: 10;
    padding: 5px;
    outline: none;
}
</style>