<template>
    <div>
        <p>Today is {{fullDate}}</p>
        <button @click="addDay">Days +</button>
        <button @click="addMonth">Month +</button>
    </div>
</template>

<script>
export default {
    name: 'TodayIs',
    data() {
        return {
            counterDay: 0,
            counterMonth: 0
        }
    },
    methods: {
        addDay: function() {
            this.counterDay++
        },
        addMonth: function() {
            this.counterMonth++
        },
    },
    computed: {
        fullDate() {
            return this.counterDay  + '.' + this.counterMonth
        }
    }
}
</script>
