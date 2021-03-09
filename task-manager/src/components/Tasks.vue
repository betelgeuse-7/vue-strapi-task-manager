<template>
    <div>
        <div v-for="task in tasks" v-bind:key="task.id">
            <Task @delete-task="deleteTask(task.id)" :task="task" />
        </div>
    </div>
</template>

<script>
    import Task from "./Task"

    export default {
        name: "Tasks",
        props: {
            tasks: Array
        },
        components: {
            Task
        },
        methods: {
            deleteTask(id){
            // Emit to "super" component (App)
                this.$emit('delete-task', id)
            }
        }
    }
</script>

