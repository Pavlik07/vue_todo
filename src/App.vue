<template>
    <div id="app">
        <h1 class="mainText">MY TASKS FOR TODAY</h1>
        <Todos v-if="todos.length" v-bind:todos="todos"/>
        <h3 class='allTasks' v-else>You have completed all the tasks</h3>
        <Form @addTask="addTodo" @submit="log"/>
        <TodayIs />
    </div>
</template>

<script>
    import Todos from './components/Todos'
    import Form from './components/Form'
    import TodayIs from './components/TodayIs'

    export default {
        name: 'App',
        data() { 
            return{
                todos: [
                    {id:1, content:'buy milk', completed: false},
                    {id:2, content:'clean the house', completed: false},
                    {id:3, content:'take out trash',completed: false}
                ]
            }
        },
        components: {
            Todos,
            Form,
            TodayIs
        },
        methods: {
            addTodo(newTodo) {
                this.todos.push(newTodo)
                localStorage.todos = this.todos
            },
            log(e) {
                console.log(e);
            }
        },
        mounted() {
            if(localStorage.todos) {
                this.todos = JSON.parse(localStorage.todos);
            }
        },
        watch: {
            todos(newTodo) {
                localStorage.todos = JSON.stringify(newTodo);
            }
        }
    }
</script>

<style scoped>
    .mainText{
        text-align: center;
    }
    .allTasks {
        text-align: center;
        color:chocolate;
    }
</style>