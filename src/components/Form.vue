<template>
    <form class="oneForm" @submit.prevent="addTask">
        <input type="text" v-model="newTask">
        <button type="submit" class="addbtn">Add Todo</button>
    </form>
</template>

<script>
export default {
    components: {
    },
    data() {
        return {
            newTask: '',
        }
    },
    methods: {
        addTask() {
            //console.log(this.newTask)
            if(this.newTask !== '') {
                const newTodo = {
                    id: Date.now(),
                    content: this.newTask,
                    completed: false,
                }
                //console.log(newTodo);
                this.newTask = '';
                this.$emit('addTask', newTodo)
            }
        }
    }
}
</script>

<style scoped>
    .oneForm {
        margin-top: 50px;
        display: flex;
        justify-content: center;
    }

    input {
        width: 500px;
        border: solid brown 1px;
    }

    .addbtn {
        margin-left: 5px;
        background-color: cyan;
    }
</style>