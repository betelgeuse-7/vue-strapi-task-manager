<template>
    <div class="task">
        <small class="task-id">{{task.id}}</small>
        <h3>{{task.text}}</h3>
        <p class="task-day"><small class="due-small-text">Due</small> {{task.day}}</p>
        <small v-if="task.reminder" class="task-reminder">Reminder on</small>
        <button @click="deleteTask(task.id)">Delete task</button>
    </div>
</template>

<style scoped>
    .task {
        width: 400px;
        border-bottom: 3px solid #000;
        border-left: 1px solid #000;
        margin: 10px 0px 15px 0px;
        padding: 15px;
        background-color: #f3f1f1;
        word-break: break-all;
    }

    .task h3 {
        font-weight: 500;
    }

    .task * {
        margin: 5px;
    }

    .task-id {
        font-weight: 600;
        font-size: 14px;
        border-bottom: 1px solid #000;
    }

    .task-reminder {
        color: #18b339;
        border-bottom: 1px solid #18b339;
    }

    .task button {
      border: none;
      outline: none;
      color: #fff;
      width: 90px;
      height: 35px;
      background-color: #d1313e;
      cursor: pointer;
      font-size: 14px;
    }

    .due-small-text {
        border-bottom: 0.5px solid #000;
        font-weight: 400;
        margin-left: 0;
    }

    .task-day {
        font-weight: 550;
    }

</style>


<script>
    export default {
        name: "Task",
        props: {
            task: Object
        },
        methods: {
            deleteTask(id) {
                // emit to the "super" component (Tasks)
                this.$emit("delete-task", id);
            }
        }
    }
</script>


