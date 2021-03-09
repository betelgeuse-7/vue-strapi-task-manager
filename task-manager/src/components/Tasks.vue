<template>
    <div>
        <div v-for="task in tasks" v-bind:key="task.id">
            <!-- Emit to "super" component (App) -->
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
                this.$emit('delete-task', id)
            }
        }
    }
</script>

