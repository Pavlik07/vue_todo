<template>
    <li class="liClass">
        <input type="checkbox" v-model='todo.completed'/>
        <span :class='{completed: todo.completed}'>{{index + 1}} {{todo.content | upperCase}}</span>
        <button 
            class="deletebtn" 
            @click="$emit('deletebtn', todo.id)"
        >  
            Delete
        </button>
    </li>
</template>

<script>
export default {
    name: 'Todoitem',
    components: {
    },
    props: {
        todo: {},
        index: Number,
    },
    filters: {
        upperCase(value) {
            return value.charAt(0).toUpperCase() + value.slice(1);
        }
    }
}
</script>

<style>
    .liClass{
        border: solid brown 1px;
        margin-top: 5px;
        margin-left: 30%;
        margin-right: 30%;
        display: flex;
        justify-content: space-between;
    }

    .completed{
        text-decoration: line-through;
    }

    .deletebtn{
        background-color: crimson;
    }
</style>