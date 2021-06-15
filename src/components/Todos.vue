<template>
        <ul>
            <TodoItem
                v-for="(todo, i) in todos" 
                :key="todo.id"
                :todo="todo"
                :index="i"
                @deletebtn="deletebtn"
            />
        </ul> 
</template>

<script>
    import TodoItem from './TodoItem'
    export default {
        components: {
            TodoItem, 
        },
        props: {
            todos: Array,
        },
        methods: {
            deletebtn(id) {
                const index = this.todos.findIndex(i => i.id===id);
                this.todos.splice(index, 1);
                //this.todos = this.todos.filter(arr => arr.id !==id);
            },
            addTodo() {
                this.todos.push(this.todo)
            }
        }
    }
</script>

<style scoped>
    ul{
        list-style: none;
        margin: 0;
        padding: 0;
    }
</style>